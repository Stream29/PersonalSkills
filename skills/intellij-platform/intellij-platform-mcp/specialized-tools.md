# IntelliJ Platform MCP Specialized Tools

Source: https://www.jetbrains.com/help/idea/mcp-server.html

Use this for official MCP tools that are useful only in specific IDE/project contexts.

## Notebooks

- Use notebook cell execution tools only for projects and IDEs with notebook support.
- Run the smallest relevant cell or cell range.
- Capture outputs concisely.
- Avoid rerunning expensive notebook cells unless requested.

## VCS

- Use repository-list tools to discover IDE VCS roots.
- Prefer IDE VCS context when the task is about how the IDE sees repositories.
- Prefer shell `git` for normal Git operations unless IDE context matters.

## Monorepo Status

- Use monorepo status tools when the project uses IDE-supported monorepo integrations.
- Do not assume a monorepo tool exists in ordinary projects.
- Summarize affected modules or status categories.

## Plugin DevKit

- Use DevKit tools only for IntelliJ Platform plugin development.
- Prefer them for plugin IDs, plugin descriptors, extension points, and plugin model questions.
- Probe tool availability before depending on DevKit-specific results.
