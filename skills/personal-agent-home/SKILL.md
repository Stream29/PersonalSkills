---
name: personal-agent-home
description: Use to edit the user's personal coding agent home configuration, especially AGENTS.md rules and skills, for Codex, OpenCode, Claude Code.
---

# Personal Agent Home

Use this skill to configure coding agents.

Use symbolic links for rules and skills. Do not copy them into agent home directories.

Keep `SKILL.md` as the directory only. Load companion files on demand:

- `GlobalAgentRules.md`: canonical `AGENTS.md` content only.
- `codex.md`: Global Codex configuration.
- `opencode.md`: Global OpenCode configuration.
- `claude-code.md`: Global Claude Code configuration.
