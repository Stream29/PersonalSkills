# IntelliJ Script MCP IDE Recipes

Use this for advanced IDE automation through `kotlin_eval`.

## Intentions And Quick Fixes

- Use editor context to find the selected editor and PSI file.
- Commit documents before collecting intentions.
- Read available actions under a read action.
- Do not invoke quick fixes automatically unless the user asked for that exact change.
- Report available fixes by family/name and affected location.

## Completion

- Prefer active editor completion when testing IDE behavior.
- Trigger completion on the EDT.
- Read lookup items immediately and hide the lookup afterward.
- For headless collection, use completion APIs only when a real completion process can be supplied.

## Search Everywhere

- Use Search Everywhere APIs when the task is specifically about IDE actions, files, classes, symbols, or text contributors.
- Query contributors directly when UI selection is unnecessary.
- Do not block the EDT waiting for Search Everywhere futures.

## Gradle Through IDE

- Use IDE Gradle APIs when validating IDE integration or project model behavior.
- Probe Gradle plugin availability first.
- Prefer async execution with polling for syncs and long tasks.
- Use shell Gradle commands for ordinary long builds unless IDE integration is the point.

## Project Model

- Use `ModuleManager` for modules.
- Use `ProjectRootManager` for SDKs, roots, and order entries.
- Use `ProjectJdkTable` for available JDKs.
- Read model data under the appropriate read action.
