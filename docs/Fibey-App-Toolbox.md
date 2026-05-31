#  Fibey Toolbox
[Live example](https://fibey-apps-ui.nicesmoke-dfb4fdf0.westus2.azurecontainerapps.io/)

This sample connects to the **Toolbox** via its **MCP (Model Context Protocol) Streamable HTTP** endpoint. The Toolbox acts as a single unified gateway to multiple operational tools — the agent makes one MCP connection, and the Toolbox dispatches calls to individual tools (inventory, work orders, FoundryIQ, status dashboard) behind the scenes.

## Architecture

```text
React UI → FastAPI Gateway → Field Ops Agent → Foundry Toolbox (MCP) → Tools
                                                       │
                                         ┌─────────────┼─────────────────┐
                                         │             │                 │
                                   Inventory MCP   Work Orders API   FoundryIQ
                                    (port 8001)     (port 8002)      (AI Search)
```


## How It Works

### Local Mode

In local mode, the agent runs in-process and connects directly to the Toolbox MCP endpoint using `MCPStreamableHTTPTool` from the Agent Framework.

The key integration point is a custom `httpx` transport that injects Azure bearer tokens on every request, including the MCP initialize handshake:

```python
from agent_framework import Agent, MCPStreamableHTTPTool
from agent_framework.foundry import FoundryChatClient

class _AzureAuthTransport(httpx.AsyncHTTPTransport):
    """Injects a bearer token on every request."""

    def __init__(self, credential, **kwargs):
        super().__init__(**kwargs)
        self._credential = credential

    async def handle_async_request(self, request: httpx.Request) -> httpx.Response:
        loop = asyncio.get_running_loop()
        token = await loop.run_in_executor(None, _get_token_sync, self._credential)
        request.headers["Authorization"] = f"Bearer {token}"
        request.headers["Foundry-Features"] = "Toolboxes=V1Preview"
        return await super().handle_async_request(request)
```

The MCP tool is created with an authenticated HTTP client and registered with the agent:

```python
def _create_toolbox_mcp(credential) -> MCPStreamableHTTPTool | None:
    toolbox_url = os.getenv("TOOLBOX_MCP_URL", "")

    auth_http_client = httpx.AsyncClient(
        transport=_AzureAuthTransport(credential),
        timeout=httpx.Timeout(60.0, connect=10.0),
    )

    def header_provider(kwargs=None) -> dict[str, str]:
        token = credential.get_token(_TOKEN_SCOPE).token
        return {
            "Authorization": f"Bearer {token}",
            "Foundry-Features": "Toolboxes=V1Preview",
        }

    return MCPStreamableHTTPTool(
        name="toolbox",
        url=toolbox_url,
        http_client=auth_http_client,
        header_provider=header_provider,
        load_prompts=False,
    )
```

### Hosted Mode

In hosted mode, the agent is deployed as a container to Foundry Agent Service. Authentication is handled automatically by the platform:

```python
from agent_framework import Agent
from agent_framework.foundry import FoundryChatClient
from agent_framework_foundry_hosting import ResponsesHostServer

def create_hosted_agent() -> Agent:
    client = FoundryChatClient()

    tools = []
    toolbox_url = os.getenv("TOOLBOX_MCP_URL", "")
    if toolbox_url:
        toolbox_mcp = client.get_mcp_tool(
            name="toolbox",
            url=toolbox_url,
            approval_mode="never_require",
        )
        tools.append(toolbox_mcp)

    agent = Agent(
        client=client,
        name="fibey",
        instructions=_load_system_prompt(),
        tools=tools,
    )
    return agent

# Serve the agent
ResponsesHostServer(agent).run()
```

## Configuration

Set the `TOOLBOX_MCP_URL` environment variable to your Toolbox MCP endpoint:

```env
# Always use the versioned URL — the endpoint defaults to v1 even if newer versions exist
TOOLBOX_MCP_URL=https://<account>.services.ai.azure.com/api/projects/<project>/toolboxes/<name>/versions/<ver>/mcp?api-version=v1
```

## Authentication Flow

```text
Azure Credential → Bearer Token → httpx Transport → MCP HTTP requests
```

The agent uses `AzureCliCredential` (local dev) or `DefaultAzureCredential` (production) scoped to `https://ai.azure.com/.default`. The custom transport intercepts every outbound HTTP request and injects a fresh token, ensuring all MCP protocol messages (initialize, tool/list, tool/call) are authenticated.

## Streaming Activity Events

When the agent calls a Toolbox tool, the streaming generator emits structured activity events so the UI can display real-time spinners and status in the activity sidebar:

```python
# Tool call detected → emit "running" event
yield {
    "type": "activity",
    "tool": tool_name,
    "call_id": call_id,
    "status": "running",
    "detail": f"Calling {tool_name}...",
}

# Tool result received → emit "complete" event
yield {
    "type": "activity",
    "tool": tool_name,
    "call_id": call_id,
    "status": "complete",
    "detail": f"Completed {tool_name}",
}
```

The agent parses tool arguments to show context-rich details like `Calling get_work_order (work_order_id=WO-1234)`.


## Key Files

| File | Description |
|------|-------------|
| `src/fibey/agent/agent.py` | Local-mode agent with Toolbox MCP connection |
| `src/fibey/agent/hosted.py` | Hosted-mode entrypoint for Foundry Agent Service |
| `src/fibey/agent/main.py` | CLI entrypoint for local interactive testing |
| `src/fibey/gateway/api_server.py` | FastAPI gateway that streams agent events as SSE |
| `.env.example` | Environment variable reference |

## Important Notes

- **Versioned URLs**: Always use the versioned Toolbox endpoint URL. The default endpoint serves v1 even after newer versions are created.
- **Feature flag**: The `Foundry-Features: Toolboxes=V1Preview` header is required during preview.
- **MCP lifecycle**: `MCPStreamableHTTPTool` must be used as an async context manager (`async with`) to properly initialize and close the MCP session.
- **Hosted vs. Local**: In hosted mode, use `client.get_mcp_tool()` which handles auth internally. In local mode, use `MCPStreamableHTTPTool` with a custom authenticated HTTP client.
