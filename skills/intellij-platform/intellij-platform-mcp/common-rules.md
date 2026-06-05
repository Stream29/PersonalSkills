# IntelliJ Platform MCP Common Rules

Source: https://www.jetbrains.com/help/idea/mcp-server.html

Use this before calling official JetBrains IntelliJ Platform MCP tools.

## Tool Choice

- Prefer official IDE MCP tools for IDE-aware project operations.
- Use CLI commands when the user asks for shell integration or MCP is unavailable.
- Use shell commands for long watch tasks, shell pipelines, or non-IDE work.
- For script-like execution, choose an official MCP route: Inspection KTS for code inspections, run configurations for executable project code, terminal commands for shell scripts, or debugger evaluation for paused runtime expressions.
- Do not assume arbitrary IDE-process script evaluation is available unless the exposed official MCP tools list contains a specific tool for it.

## Namespace And Project

- Use the MCP namespace that belongs to the active IDE project.
- Pass `projectPath` whenever the project root is known.
- Ask which IDE owns the project when several JetBrains IDE MCP namespaces are available.
- Do not guess MCP ports, URLs, server names, launcher names, or IDE ownership.

## Paths And Positions

- Use project-relative paths unless a tool explicitly accepts absolute paths or returned archive/URL paths.
- Keep paths returned by MCP tools unchanged when feeding them into another MCP tool.
- Treat line and column values as 1-based.
- Use glob filters to avoid broad searches in generated or vendored directories.

## Safety

- Avoid mutating files, database data, breakpoints, or run configurations unless the user asked for that work.
- Prefer semantic tools over plain text operations when changing code symbols.
- Validate meaningful edits with file problems, run configurations, tests, or formatting.
- Summarize large outputs instead of pasting full logs, SQL, or inspection reports.
