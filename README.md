# 🚀 Get Started

**This repo is where attendees go to continue their learning after your session — and your Copilot agent will help you set it up.**

### Step 1: Open your repo

Open this repo in a **Codespace** (click the green **Code** button → **Create a Codespace**) — or clone it locally. Then open **GitHub Copilot Chat**.

### Step 2: Add your content

Give the agent something to work with. Drag files into the Explorer panel — session abstracts, outlines, screenshots, notes — and drop them in one of two places:

| Where to put it | What goes there | Who sees it |
|---|---|---|
| **`_remove-before-publish/`** | Internal reference materials (abstracts, outlines, screenshots, planning docs) | **Copilot only** — never published |
| **`/docs/`, `/src/`, or repo root** | Lab instructions, demo code, sample data, getting-started guides | **Attendees** — published with the repo |

> 💡 Not sure? Start by dropping your session abstract or outline into `_remove-before-publish/`. The agent will figure out what to do with it.

### Step 3: Ask the Agent

Once your content is in the repo, use these three phrases with Copilot to build out your session repo:

| Phrase to use with Copilot | What it does | When to run it |
|---|---|---|
| **"Help me get started"** | Sets up session title, description, outcomes, and owners | After you've added your session abstract or outline to the repo |
| **"Help me refine content"** | Organizes your session content into the repo | Each time you add or update content |
| **"Help me finalize"** | Final review, cleanup, and publication prep | When you're ready to publish |

> 💡 **These three phrases are just the starting point.** Copilot can do much more — try asking it to brainstorm next steps for attendees, generate code samples, or build out your repo structure. Don't be afraid to put it in plan mode and ask for what you need.

---

<a name="start-building"></a>
<br>
<p align="center">
<img src="img/banner-build-26.png" alt="Microsoft Build 2026" width="1200"/>
</p>

# [Microsoft Build 2026](https://build.microsoft.com)

## 🔥 BRK242: Turn your agents into action: Connect tools, APIs, and documents

### Session Description

Tired of searching for the right tools for your agents, or watching your context window grow out of control? This breakout introduces a new product category that helps developers choose the right toolset based on an agent's context, use case, and functional boundaries so teams can connect tools efficiently with built-in governance.

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

### 💬 Keep Learning with Copilot

Try these prompts with GitHub Copilot to explore the topics from this session. Open Copilot Chat in VS Code (`Ctrl+Alt+I` on Windows/Linux, `Cmd+Shift+I` on Mac), paste a prompt, and see what you learn. Try connecting the [Microsoft Learn MCP Server](#-microsoft-learn-mcp-server) for the latest official documentation.

Use these as a starting point — or write your own!

Try prompts like:

- "Help me design an agent tool strategy for a customer support scenario using APIs and documents."
- "Compare when to call an API directly vs. route through a tool abstraction in an agent workflow."
- "Show me a practical pattern to keep agent context windows small while still grounding on documents."
- "Generate a governance checklist for agent tool access, data boundaries, and auditing."

### 💻 Technologies Used

1. [Azure AI Foundry](https://learn.microsoft.com/azure/ai-foundry/)
1. [Azure AI Foundry Agent Service](https://learn.microsoft.com/azure/ai-foundry/agents/)
1. [Model Context Protocol (MCP) tools in Azure AI Foundry Agent Service](https://learn.microsoft.com/azure/ai-foundry/agents/how-to/tools/model-context-protocol)

### 📚 Resources and Next Steps

| Resource | Description |
|:---------|:------------|
| [https://aka.ms/build26-next-steps](https://aka.ms/build26-next-steps) | Explore lab and session repos to further your learning from Microsoft Build |


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
