<p align="center">
  <img src="icon.png" alt="SpecificAI" width="64" height="64">
</p>

<h1 align="center">SpecificAI MCP server</h1>

<p align="center">
  Train, evaluate and deploy task-specific models on <a href="https://specific.ai">SpecificAI</a> from your AI agent.
</p>

The SpecificAI MCP server lets an AI agent such as Cursor, Claude Code, VS Code or Codex work with the SpecificAI platform over the [Model Context Protocol](https://modelcontextprotocol.io). It is hosted, so there is nothing to install or run: add the endpoint to your agent and sign in.

| | |
|---|---|
| Endpoint | `https://app.specific.ai/api/mcp` |
| Transport | Streamable HTTP |
| Sign-in | Your SpecificAI account, in the browser, the first time the agent connects |

A self-hosted SpecificAI platform serves the same server at `https://<your platform address>/api/mcp`. Its **Settings → MCP** page shows that address, with connect links for it.

## What your agent can do

- Look up your projects, tasks, datasets, and running and recent work: trainings, evaluations, uploads and data generation
- Create tasks, upload dataset files from your machine or import Hugging Face datasets, and generate or source more training data
- Start trainings with the same options as the Train page, and read their evaluations
- Query a trained model next to its teacher, then deploy, undeploy or download it
- Stop running work and delete datasets

That is enough to go from a local file or a Hugging Face dataset to a deployed model without leaving the chat, and every result suggests what to do next. **Settings → MCP → View Tools** in the platform lists every tool.

## Connect your agent

### Cursor

[![Add to Cursor](https://cursor.com/deeplink/mcp-install-dark.svg)](https://cursor.com/install-mcp?name=specific-ai&config=eyJ1cmwiOiJodHRwczovL2FwcC5zcGVjaWZpYy5haS9hcGkvbWNwIn0%3D)

### VS Code

```bash
code --add-mcp '{"name":"specific-ai","type":"http","url":"https://app.specific.ai/api/mcp"}'
```

VS Code asks you to sign in the first time it starts the server.

### Claude Code

```bash
claude mcp add --transport http specific-ai https://app.specific.ai/api/mcp
```

Then run `/mcp` in Claude Code and choose **Authenticate**.

### Codex

```bash
codex mcp add specific-ai --url https://app.specific.ai/api/mcp
```

Codex opens the sign-in. To sign in again later, run `codex mcp login specific-ai`.

### Gemini CLI

```bash
gemini mcp add --transport http specific-ai https://app.specific.ai/api/mcp
```

Then run `/mcp auth specific-ai` inside Gemini CLI.

### Grok Build

```bash
grok mcp add --transport http specific-ai https://app.specific.ai/api/mcp
```

Grok opens the sign-in in your browser the first time it uses the server.

### Claude

In claude.ai, open [Customize → Connectors](https://claude.ai/customize/connectors) and add a custom connector named SpecificAI with the URL `https://app.specific.ai/api/mcp`. On a Team or Enterprise plan only an Owner can add it, under **Organization settings → Connectors**; members then click **Connect** under **Customize → Connectors**.

### Any other agent

Ask it in the chat:

```text
Add this MCP server as a custom connector named SpecificAI: https://app.specific.ai/api/mcp
```

Or add this block to its MCP configuration:

```json
{
  "mcpServers": {
    "specific-ai": {
      "type": "http",
      "url": "https://app.specific.ai/api/mcp"
    }
  }
}
```

## Sign-in and access

- **No API key.** The first time your agent connects, it opens the SpecificAI sign-in page in your browser, then a consent page that lists the workspaces the agent will reach and its role in each.
- **It acts as you,** only in the workspaces you open to MCP clients under **Settings → MCP → Workspace access**, with at most Editor rights and never more than your own role.
- **Revoke it any time** under **Settings → MCP → Connected**. The agent then has to sign in again.
- **Agents that can't open a browser,** such as CI jobs and servers, can't connect. Use a SpecificAI SDK with an API key instead: [Python](https://pypi.org/project/specific-ai/), [JavaScript](https://www.npmjs.com/package/specific-ai) or [Go](https://github.com/marketplace-specificai/go-specific-ai-sdk).

## About this repository

The server runs inside the SpecificAI platform. This repository holds its public documentation and [`server.json`](server.json), its entry for MCP registries.

## License

[Apache License 2.0](LICENSE)
