---
name: personal-agent-home
description: Use to edit the user's personal coding agent home configuration, especially AGENTS.md rules and skills, for Codex, OpenCode, Claude Code.
---

# Personal Agent Home

Use this skill to configure coding agents.

Use symbolic links for rules and skills. Do not copy them into agent home directories.

Use `~/.agent` as the shared local agent home:

- Link repository-managed rules and skills into `~/.agent`.
- Put machine-local shared skills directly under `~/.agent/skills`.
- Link each agent home's rules and whole `skills` directory back to `~/.agent`.

Keep `SKILL.md` as the directory only. Load companion files on demand:

- `assets/AGENTS.md`: canonical global agent rules.
- `agent-home.md`: Shared local agent home layout.
- `codex.md`: Global Codex configuration.
- `opencode.md`: Global OpenCode configuration.
- `claude-code.md`: Global Claude Code configuration.
