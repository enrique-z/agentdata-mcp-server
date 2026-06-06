## Design System
Always read DESIGN.md before making any visual or UI decisions.
All font choices, colors, spacing, and aesthetic direction are defined there.
Do not deviate without explicit user approval.
In QA mode, flag any code that doesn't match DESIGN.md.

## Skill routing

When the user's request matches an available skill, invoke it via the Skill tool. When in doubt, invoke the skill.

Key routing rules:
- Product ideas/brainstorming → invoke /office-hours
- Strategy/scope → invoke /plan-ceo-review
- Architecture → invoke /plan-eng-review
- Design system/plan review → invoke /design-consultation or /plan-design-review
- Full review pipeline → invoke /autoplan
- Bugs/errors → invoke /investigate
- QA/testing site behavior → invoke /qa or /qa-only
- Code review/diff check → invoke /review
- Visual polish → invoke /design-review
- Ship/deploy/PR → invoke /ship or /land-and-deploy
- Save progress → invoke /context-save
- Resume context → invoke /context-restore

## Public Marketing Repository
**CRITICAL FOR ALL AGENTS:** The local codebase on this Mac (`/Users/apple/code/apps/b2b-agent-api`) is the strictly PUBLIC marketing and SEO repository (mapped to `agentdata-mcp-server` on GitHub). 
**DO NOT** place any backend code, API keys, research documents, or Agent-OS specifications here. All actual backend infrastructure and confidential data resides in the PRIVATE repository at `/Users/apple/code/apps/agentdata-code`.

## Remote Server Architecture Mapping
- **VPS Hostname:** `SUPserver-ssdnodes` (IP: 199.241.138.217)
- **Production Directory:** `/opt/b2b-agent-api/`
- **Database:** Runs in a Docker volume on the VPS (`b2b_agent_db`). Do NOT attempt to run local database migrations without SSHing into the remote environment.
