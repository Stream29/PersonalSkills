---
name: idea
description: "Use when working with IntelliJ IDEA, including its MCP server, CLI, debugger, database tools."
---

# IntelliJ IDEA

## IDEA MCP

Treat the IDE's Exposed Tools list as the source of truth. Availability depends on the IDE version, enabled plugins, and MCP settings.

- Prefer native agent tools for database access, file operations, patches, reads, VCS, and terminal commands. Do not use Database-specific, Patch, Read, Terminal, or VCS tools, or File tools other than `open_file_in_editor`; IDEA terminal execution also has timeout and output constraints.
- Discover additional plugin-provided toolsets only when needed.
- Use `execute_tool` for tools exposed only through router-only mode.

## IDEA CLI

- Run `idea --help` for basic commands and options.
- Run `idea --list-commands` for commands exposed by the current installation.
- Run `idea --version` before giving version-sensitive guidance.
