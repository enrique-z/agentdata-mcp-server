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

## Remote Server Architecture Mapping
**CRITICAL FOR ALL AGENTS:** The local codebase on this Mac (`/Users/apple/code/apps/b2b-agent-api`) is the development repository. However, the **live production application** resides on a remote VPS.
- **VPS Hostname:** `SUPserver-ssdnodes` (IP: 199.241.138.217)
- **Production Directory:** `/opt/b2b-agent-api/`
- **Deployment Protocol:** Changes made locally must be committed to GitHub (`origin/master`), and then deployed to the VPS via SSH (`ssh SUPserver-ssdnodes 'cd /opt/b2b-agent-api && git pull'`).
- **Database:** Runs in a Docker volume on the VPS (`b2b_agent_db`). Do NOT attempt to run local database migrations without SSHing into the remote environment.
- **Agent-OS Documentation:** Review `.agent-os/specs/` and `.agent-os/standards/` for detailed architectural, monetization, and security directives.
