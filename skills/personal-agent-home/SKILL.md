---
name: personal-agent-home
description: Use to edit the user's personal coding agent home configuration, especially AGENTS.md rules and skills, for Codex, OpenCode, Claude Code.
---

# Personal Agent Home

- Share rules and skills through symbolic links, not copies, using `~/.agents` as the shared local home.
- Link repository-managed rules and skills into `~/.agents`; store machine-local shared skills directly under `~/.agents/skills`.
- Link each agent's rules and whole skills directory back to the shared home; discover agent-specific paths when needed.
- [assets/AGENTS.md](assets/AGENTS.md) is the canonical global rules source; read it when editing rules.
