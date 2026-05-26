# IntelliJ Platform MCP Project Analysis

Source: https://www.jetbrains.com/help/idea/mcp-server.html

Use this for project structure, build status, dependencies, modules, symbols, and file diagnostics.

## Build And Diagnostics

- Use `build_project` when the user needs the IDE build result.
- Use `get_file_problems` for errors and warnings in one file.
- Pass `errorsOnly=true` for compile-blocking checks.
- Include warnings when code quality or IDE inspection feedback matters.
- Use timeouts for large files or analysis-heavy projects.

## Project Model

- Use `get_project_modules` to discover modules.
- Use `get_project_dependencies` to inspect project dependency information.
- Use project model tools before guessing Gradle/Maven/IDE module layout.
- Treat IDE model as source of truth for configured SDKs, dependencies, generated roots, and source roots.

## Symbol Info

- Use `get_symbol_info` to inspect the declaration, type, signature, docs, or resolved target at a file position.
- Use it before editing unfamiliar APIs, overloads, extension functions, framework entry points, or generated symbols.
- Pass project-relative file path plus 1-based line and column.

## Work Pattern

- First identify the project and module context.
- Then inspect symbols or file problems at the smallest useful scope.
- Run broader build or inspection tools only when the user asks or the blast radius requires it.
