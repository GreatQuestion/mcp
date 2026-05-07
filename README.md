# Great Question MCP Server

<!-- mcp-name: io.github.greatquestion/mcp -->

Run user research from any AI tool. The official Model Context Protocol (MCP) server for [Great Question](https://greatquestion.co) — the AI UX research platform for product builders.

Once connected, Claude, ChatGPT, Cursor, Windsurf, Gemini CLI, and any other MCP-compatible client can create research studies, recruit participants, and query insights directly from your Great Question workspace.

> *"The Great Question MCP surfaces insight across studies in minutes, not days. It brings real customer patterns into discovery when decisions are happening, so we can act with confidence and build what matters most."*
> — **Matt Radel**, VP of Design & UX at InvoiceCloud

---

## What it does

This is not a read-only research lookup tool. AI agents connected to this server can actively run research workflows:

- 🎤 **Create moderated interview studies** from a single prompt
- 📝 **Build multi-question surveys** without leaving the conversation
- 🧪 **Set up prototype tests** with screeners, scheduling, and incentives
- 🎯 **Search your customer CRM** to identify the right participants for each study
- 🔍 **Query your research repository** for insights, summaries, and reports across past sessions, transcripts, and tags

## Who it's for

- **Product managers** bringing the customer voice into PRDs and discovery work
- **UX researchers** scaling research programs without scaling hands-on coordination
- **Designers** referencing past usability findings while building new flows
- **Research ops teams** streamlining workflows across studies and repositories
- **Founders** doing product discovery without a dedicated research function

## Setup

### Prerequisites

- A [Great Question](https://greatquestion.co) workspace (any plan)
- An MCP-compatible client (Claude Desktop, Claude Code, Cursor, Windsurf, ChatGPT, Gemini CLI, or any other)

### Installation

The Great Question MCP is hosted — there is nothing to install locally. You add it to your MCP client by pointing it at our endpoint:

```
https://greatquestion.co/api/mcp/v1
```

### Claude Code

```bash
claude mcp add --transport http great-question https://greatquestion.co/api/mcp/v1
```

### Claude Desktop

Open Claude Desktop → Settings → Developer → Edit Config, then add:

```json
{
  "mcpServers": {
    "great-question": {
      "type": "http",
      "url": "https://greatquestion.co/api/mcp/v1"
    }
  }
}
```

Restart Claude Desktop. You'll be prompted to authorize via OAuth on first use.

### Cursor

Cursor → Settings → MCP → Add new MCP server:

```json
{
  "mcpServers": {
    "great-question": {
      "url": "https://greatquestion.co/api/mcp/v1"
    }
  }
}
```

### Windsurf

Windsurf Settings → Cascade → MCP Servers → Add custom server with URL `https://greatquestion.co/api/mcp/v1`. Windsurf supports OAuth automatically.

### ChatGPT

In ChatGPT, go to Settings → Connectors → Add connector. Use the URL `https://greatquestion.co/api/mcp/v1`. You'll be prompted to sign in via OAuth.

### Gemini CLI

```bash
gemini extensions install https://github.com/GreatQuestion/mcp
```

### Other MCP clients

Any MCP client that supports remote (HTTP) servers can connect using the URL `https://greatquestion.co/api/mcp/v1`. Authentication is OAuth 2.0.

## Authentication & security

- **OAuth 2.0** — credentials are never exposed to the AI client. You sign in to Great Question on first connection; the AI agent receives a scoped access token.
- **Role-based permissions** — every action respects the role you have in your Great Question workspace. If you can't create studies in the UI, you can't create them via the MCP either.
- **SOC 2 Type II compliant** — Great Question maintains an active SOC 2 Type II attestation; the MCP inherits the same controls as the rest of the platform.
- **Workspace isolation** — your data never crosses workspace boundaries.

## Example prompts

Here are some prompts that work well with the Great Question MCP. They're meant as a starting point — the server exposes the full set of research workflows, so phrasing is flexible.

- *"Create a moderated interview study about checkout abandonment, 6 participants from our enterprise customers, 30 minutes, $100 incentive."*
- *"Find the 5 most-mentioned pain points across our usability tests from the last 90 days."*
- *"Recruit 10 PMs from our CRM who fit our ICP for a survey on AI tool adoption."*
- *"Summarize what we've heard from customers about our pricing in the last quarter."*
- *"Pull every quote from our research repository where someone mentions [feature name]."*

## Tools exposed

The server exposes the following toolsets. Tool names and exact arguments are discovered automatically by your MCP client — this list is for orientation.

- **Studies** — list, create, configure, and launch interview studies, surveys, and prototype tests
- **Participants** — search your customer CRM, segment by attributes, generate participant lists for studies
- **Scheduling & screeners** — configure availability, screening questions, and incentive structures
- **Repository search** — full-text and semantic search across past sessions, transcripts, highlights, and tags
- **Insights & reports** — query existing reports and generate summaries across multiple studies

## Resources

- **Landing page:** [greatquestion.co/features/mcp-integration](https://greatquestion.co/features/mcp-integration)
- **Great Question:** [greatquestion.co](https://greatquestion.co)
- **Endpoint:** `https://greatquestion.co/api/mcp/v1`
- **MCP namespace:** `io.github.greatquestion/mcp`
- **Status:** Live production
- **Transport:** Streamable HTTP
- **Auth:** OAuth 2.0

## Support

- **Bugs and feature requests:** [open an issue](https://github.com/GreatQuestion/mcp/issues)
- **Customer support:** support@greatquestion.co
- **Security disclosures:** security@greatquestion.co

## License

MIT — see [LICENSE](LICENSE).
