---
name: intellij-platform
description: "Use when working with JetBrains IntelliJ Platform IDEs."
---

# IntelliJ Platform

Use this skill for JetBrains IntelliJ Platform IDEs.

## Index

- Official IDE MCP:
  - `intellij-platform-mcp/install.md`: install, enable, and connect the official JetBrains MCP server.
  - `intellij-platform-mcp/common-rules.md`: project selection, path rules, tool choice, and safety.
  - `intellij-platform-mcp/project-analysis.md`: project model, dependencies, modules, symbols, and file problems.
  - `intellij-platform-mcp/files-editing.md`: read files, create files, replace text, format, open editors, and rename.
  - `intellij-platform-mcp/search-navigation.md`: find files, search text/regex/symbols, and inspect open files.
  - `intellij-platform-mcp/run-terminal.md`: run configurations, gutter run points, and terminal commands.
  - `intellij-platform-mcp/script-execution.md`: official script-like execution through inspection.kts, terminal scripts, run configurations, and debugger expressions.
  - `intellij-platform-mcp/inspection-kts.md`: Inspection KTS API, examples, PSI trees, and validation.
  - `intellij-platform-mcp/debugging.md`: debugger sessions, breakpoints, tracepoints, and stepping.
  - `intellij-platform-mcp/database.md`: database connections, schemas, objects, queries, previews, and cancellation.
  - `intellij-platform-mcp/specialized-tools.md`: notebooks, VCS roots, DevKit, and monorepo status tools.
- CLI:
  - `intellij-platform-cli/overview.md`: official CLI scope, command list, and option list.
  - `intellij-platform-cli/launchers.md`: Toolbox and standalone command-line launchers.
  - `intellij-platform-cli/open-files-projects.md`: open files, folders, projects, line, column, and wait.
  - `intellij-platform-cli/diff-merge.md`: diff viewer and merge dialog commands.
  - `intellij-platform-cli/format.md`: command-line formatter.
  - `intellij-platform-cli/inspect.md`: command-line inspections.
  - `intellij-platform-cli/plugins.md`: command-line plugin installation.
  - `intellij-platform-cli/startup-options.md`: startup recovery and launcher options.

## Boundaries

- Prefer IDE MCP tools for IDE-aware project operations.
- Use CLI commands when the user asks for shell integration or MCP is unavailable.
- Do not use IDE MCP tools for shell commands.
- Do not guess MCP ports, URLs, IDE ownership, launcher names, plugin IDs, or product-specific APIs.
