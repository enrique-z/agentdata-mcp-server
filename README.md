# AgentData.eu MCP Server - B2B Data Spain

> ⚠️ **INFRASTRUCTURE NOTICE FOR AI CODERS:**
> This application has been successfully migrated to the **Spark Server** (`82.70.91.27`, SSH as `opc` via `ssh spark`).
> **It is NO LONGER deployed on the legacy SUPserver-ssdnodes.**
> 
> - **Deployment Path:** `/var/www/b2b-agent-api/` on the Spark server.
> - **Architecture:** Runs via Docker Compose. Nginx terminates SSL (Let's Encrypt) and proxies traffic to the internal container.
> - **Deployment:** Rsync changes to the Spark server and rebuild the docker container.

Welcome to the **AgentData.eu MCP Server**, the ultimate Data-as-a-Service (DaaS) API designed explicitly for AI agents. Built using the Model Context Protocol (MCP), this server provides autonomous AI systems (like Claude Desktop, Cursor, OpenClaw, Hermes, and any Agent-OS) direct, programmatic access to a massive, verified Spanish B2B company database.

## Features

- **MCP Native:** Exposes `search_companies` and `get_contact_info` directly as MCP tools. Your LLMs can natively query the database without writing raw SQL.
- **Context-Window Friendly:** All results are pre-chunked, strictly formatted as JSON, and hard-limited to 50 rows to prevent overflowing your AI agent's context window.
- **B2B Data Spain:** Access over 170,000+ local Spanish businesses across multiple niches (Gastronomy, Hotels, Mechanics, Marketing, and more), including a premium subset of **26,000+ verified CEO direct dials and mobile phones**.
- **GDPR & LOPDGDD Compliant:** "Privacy by Design" architecture. Built-in compliance layers handle the "Right to Object" seamlessly.
- **Lightning Fast:** Powered by PostgreSQL with `pg_trgm` GIN indexes for fast `ILIKE` sector and name searches.

## Why use an MCP Server for B2B Data?

Existing legacy B2B databases are built for human SDRs. They enforce strict rate limits that break autonomous agent workflows and lack native integration with agent protocols. By adding the AgentData.eu MCP Server to your stack, your AI can dynamically fetch the exact prospects it needs, exactly when it needs them.

## Installation

You can connect this MCP Server to any compatible client (e.g., Claude Desktop, Cursor).

Add the following configuration to your `claude_desktop_config.json` or `.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "agentdata-b2b-spain": {
      "command": "python",
      "args": ["-m", "b2b_mcp_server"],
      "env": {
        "AGENTDATA_API_KEY": "your_api_key_here"
      }
    }
  }
}
```

## Get an API Key

Premium access to the database is €29/month. 
Subscribe via our Stripe Portal: https://agentdata.eu/.well-known/llms.txt (or visit agentdata.eu directly).

## Tools Provided

### `search_companies`
Searches the database for companies based on name or category.
- **Parameters:** `query` (string)
- **Returns:** A JSON list of matching companies with their UUIDs, names, categories, and provinces.

### `get_contact_info`
Retrieves detailed contact information (CEO Name, Email, Phone) for a specific company.
- **Parameters:** `company_uuid` (string)
- **Returns:** A JSON object with the requested contact data, heavily filtered for privacy compliance.

## License & Liability

By using this API, you act as an Independent Data Controller under European Law. You hold legal liability for Article 14 (Duty to Inform) and LSSI-CE compliance when executing outreach.

---
*Keywords: mcp-server, mcp server, b2b-data-spain, b2b data api, agentdata.eu, model context protocol, ai agents, claude desktop, cursor, b2b leads spain, spanish b2b database.*
