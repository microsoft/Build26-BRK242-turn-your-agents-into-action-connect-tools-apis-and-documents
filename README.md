<a name="start-building"></a>
<br>
<p align="center">
<img src="img/banner-build-26.png" alt="Microsoft Build 2026" width="1200"/>
</p>

# [Microsoft Build 2026](https://build.microsoft.com)

## 🔥 BRK242: Turn your agents into action: Connect tools, APIs, and documents

## 📑 Table of Contents

The two product pillars of this session — and where to dive deeper:

| # | Pillar | What you'll learn | Where to go |
|---|---|---|---|
| 1 | **🧰 Toolbox** | Bundle every tool an agent needs (MCP, A2A, OpenAPI, connectors, built-ins) behind one governed endpoint that any framework can call. | [What is a Toolbox](#what-is-a-toolbox) · [Fibey App Toolbox sample](docs/Fibey-App-Toolbox.md) |
| 2 | **📄 Azure Content Understanding in Foundry Tools** | Turn messy, multimodal content (PDFs, images, audio, video, Office docs) into structured, agent-ready output — building on the foundation of **Azure Document Intelligence**. | [What is Content Understanding](#what-is-content-understanding) · [Fiberly demo with Content Understanding integrated (fiberly-agent-cu repo)](https://github.com/jfilcik/fiberly-agent-cu) |

**Other sections:** [Session Description](#session-description) · [Learning Outcomes](#-learning-outcomes) · [Getting Started](#-getting-started) · [Keep Learning with Copilot](#-keep-learning-with-copilot) · [Technologies Used](#-technologies-used) · [Resources](#-resources-and-next-steps) · [Microsoft Learn MCP Server](#-microsoft-learn-mcp-server) · [Content Owners](#content-owners)

### Session Description

Tired of searching for the right tool(s) for your agents? Seeing your context window constantly blowing out of proportion? We are introducing a new product category that allows developers to choose the right toolset depending upon the agents' context, the use-case and functional boundaries, enabling efficient use of tools, with built-in governance.

Seating for this session is first-come, first-served. Add it to your schedule to plan your day and arrive early to secure a spot

### Turn Your Agents Into Action

Why: Today, most agents look impressive in demos—but break in production. They rely on bloated prompts, fragile integrations, and struggle with real-world data like PDFs, receipts, or emails. In this session, we'll share how to move beyond prompt-based agents to real systems that act. Sharing how to connect agents to tools, automate workflows across runtimes, and handle messy, unstructured data with confidence.

Problem: Today, most agents look impressive in demos—but break in production. They rely on bloated prompts, fragile integrations, and struggle with real-world data like PDFs, receipts, or emails.
In this repo, we'll show how to move beyond prompt-based agents to real systems that act. You'll learn how to connect agents to tools, across agent runtimes, through a single endpoint with **Toolboxes**, and how — with **Content Understanding** — you can work with unstructured data with confidence.

### What is a Toolbox

Toolbox bundles everything an agent needs into a reusable package—delivered through one endpoint with a consistent interface, no matter the tool type, managed on Foundry.

**What tool types does Toolbox support?** Toolbox is designed to be tool-agnostic:

| Category | Tool Type |
|---|---|
| Protocol-based | MCP, A2A |
| API Integration | OpenAPI, Connectors |
| Agent Instructions | Skills |
| Built-in tools | Web Search, Code Interpreter, File Search, Azure Search |

📘 **Deep dive:** [Fibey App Toolbox — an end-to-end sample using the Toolbox MCP endpoint](docs/Fibey-App-Toolbox.md).

### What is Content Understanding

**Azure Content Understanding in Foundry Tools** turns unstructured, multimodal content into reliable, structured outputs you can automate against. Content Understanding uses a consistent **Parse → Classify → Extract** taxonomy across documents, images, audio, and video:

- **Parse** — normalize raw content into usable structure: text, layout, tables, transcription, and visual elements.
- **Classify** — identify document or content types, route content, and segment it when needed.
- **Extract** — produce schema-based fields (JSON) or markdown with confidence scores and grounding.

> **Built on the foundation of Azure Document Intelligence.** Azure Content Understanding brings together Document Intelligence's industry-leading OCR, layout, and table-extraction technology — refined over many years — and extends it with LLM-powered multimodal capabilities across audio, video, and image. If you've trusted Document Intelligence for documents, Content Understanding is the natural next step: the same proven engine, now with one schema-driven API for every modality. Document Intelligence remains GA — there's no forced migration; new content-to-JSON projects should start with Content Understanding.

🚀 **Deep Dive:** Check out the [Fiberly demo with Content Understanding integrated (fiberly-agent-cu repo)](https://github.com/jfilcik/fiberly-agent-cu) to see these patterns in an end-to-end agent experience.

Content Understanding helps agents with stronger grounding, real-time context, and business-ready extraction:

- **Better grounding for RAG** — with Foundry IQ as standard, Content Understanding parses PDFs at index time, preserving structure like tables, headings, and figures.
- **Real-time context provider** — parses incoming files as the agent runs, keeps structure intact for more accurate answers, and supports a wider range of file types.
- **Business-specific extraction** — uses analyzers you define for target document types (for example, invoices, work orders, or contracts) so files can be classified, routed, and parsed for the exact values you need.

A tool lets an agent take action; Content Understanding provides the context behind that action with minimal configuration and at agent scale.

📘 **Additional info:** [Content Understanding — framework, demos, and how to use it](docs/content-understanding/README.md) · [Try Content Understanding in Foundry quickstart](docs/content-understanding/try-in-foundry.md).

### 🚀 Getting started

If you're following these steps at your own pace:

- Clone this repository
- Set up your development environment
- Explore the resources in this README and use the Copilot prompts below to design your own agent integration approach

### 🧠 Learning Outcomes

By the end of this session, you will be able to:

- Evaluate which tools, APIs, and document sources are best suited for different agent scenarios
- Design agent boundaries that keep context efficient and reduce unnecessary token usage
- Apply governance-oriented patterns when connecting agents to external systems and enterprise knowledge
- Use Content Understanding to turn multimodal, unstructured content into structured, agent-ready inputs

### 💬 Keep Learning with Copilot

Try these prompts with GitHub Copilot to explore the topics from this session. Open Copilot Chat in VS Code (`Ctrl+Alt+I` on Windows/Linux, `Cmd+Shift+I` on Mac), paste a prompt, and see what you learn. Try connecting the [Microsoft Learn MCP Server](#-microsoft-learn-mcp-server) for the latest official documentation.

Use these as a starting point — or write your own!

Try prompts like:

- "Help me design an agent tool strategy for a customer support scenario using APIs and documents."
- "Compare when to call an API directly vs. route through a tool abstraction in an agent workflow."
- "Show me a practical pattern to keep agent context windows small while still grounding on documents."
- "Generate a governance checklist for agent tool access, data boundaries, and auditing."
- "Walk me through how Content Understanding builds on Document Intelligence, and when I should pick one over the other."

### 💻 Technologies Used

1. [Azure AI Foundry](https://learn.microsoft.com/azure/ai-foundry/)
1. [Azure AI Foundry Agent Service](https://learn.microsoft.com/azure/ai-foundry/agents/)
1. [Model Context Protocol (MCP) tools in Azure AI Foundry Agent Service](https://learn.microsoft.com/azure/ai-foundry/agents/how-to/tools/model-context-protocol)
1. [Azure AI Content Understanding](https://learn.microsoft.com/azure/ai-services/content-understanding/overview)
1. [Azure AI Document Intelligence](https://learn.microsoft.com/azure/ai-services/document-intelligence/overview)

### 📚 Resources and Next Steps

| Resource | Description |
|:---------|:------------|
| [https://aka.ms/build26-next-steps](https://aka.ms/build26-next-steps) | Explore lab and session repos to further your learning from Microsoft Build |
| [Content Understanding deep-dive](docs/content-understanding/README.md) | Framework overview and pointers to Content Understanding resources |
| [Try Content Understanding in Foundry](docs/content-understanding/try-in-foundry.md) | Quickstart: Foundry Playground → Content Understanding Studio |
| [Fibey App Toolbox](docs/Fibey-App-Toolbox.md) | End-to-end sample agent wired to a Foundry Toolbox via MCP |

### 🌟 Microsoft Learn MCP Server

The Microsoft Learn MCP Server gives your AI agent direct access to Microsoft's official documentation — grounded, up-to-date answers about the products and services covered in this session.

**VS Code** — One click installation:

[![Install in VS Code](https://img.shields.io/badge/VS_Code-Install_Microsoft_Learn_MCP-0098FF?style=flat-square&logo=visualstudiocode&logoColor=white)](https://vscode.dev/redirect/mcp/install?name=microsoft-learn&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Flearn.microsoft.com%2Fapi%2Fmcp%22%7D)


**GitHub Copilot CLI** — Run this to install the Learn MCP Server as a plugin:
```
/plugin install microsoftdocs/mcp
```

For more info, other clients, and to post questions, visit the [Learn MCP Server repo](https://aka.ms/learnmcp).

## Content Owners

<table>
<tr>
     <td align="center"><a href="https://github.com/ladynaggaga">
        <img src="https://github.com/ladynaggaga.png" width="100px;" alt="Maria Naggaga"/><br />
        <sub><b>Maria Naggaga</b></sub></a><br />
            <a href="https://github.com/ladynaggaga" title="talk">📢</a>
    </td>
    <td align="center"><a href="https://github.com/jfilcik">
        <img src="https://github.com/jfilcik.png" width="100px;" alt="Joe Filcik"/><br />
        <sub><b>Joe Filcik</b></sub></a><br />
            <a href="https://github.com/jfilcik" title="talk">📢</a>
    </td>


</tr></table>

## Contributing

This project welcomes contributions and suggestions.  Most contributions require you to agree to a
Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us
the rights to use your contribution. For details, visit [Contributor License Agreements](https://cla.opensource.microsoft.com).

When you submit a pull request, a CLA bot will automatically determine whether you need to provide
a CLA and decorate the PR appropriately (e.g., status check, comment). Simply follow the instructions
provided by the bot. You will only need to do this once across all repos using our CLA.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.

## Trademarks

This project may contain trademarks or logos for projects, products, or services. Authorized use of Microsoft
trademarks or logos is subject to and must follow
[Microsoft's Trademark & Brand Guidelines](https://www.microsoft.com/legal/intellectualproperty/trademarks/usage/general).
Use of Microsoft trademarks or logos in modified versions of this project must not cause confusion or imply Microsoft sponsorship.
Any use of third-party trademarks or logos are subject to those third-party's policies.
