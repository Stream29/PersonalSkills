# IntelliJ Script MCP Kotlin Eval

Use this for `kotlin_eval` in IDE script MCP namespaces such as `mcp__idea_script__` and `mcp__webstorm_script__`.

## When To Use

- Use structured IntelliJ Platform MCP tools first when they cover the task.
- Use `kotlin_eval` for deeper IntelliJ Platform API access through the IDE script MCP.
- Use it for PSI, VFS, editor state, project model, intentions, completion, Search Everywhere, or IDE-integrated Gradle work.
- Do not use it just to run shell commands.

## Project Selection

- Pass `projectPath` when the project root is known.
- Use `projectName` only when path selection is unavailable.
- Avoid relying on the first open project when multiple projects may be open.

## Return Contract

- Return data as the final expression.
- Do not rely on `println`; stdout and stderr are not returned as tool output.
- Return concise strings or small structured values.
- For long lists, return counts and the most relevant entries.

## State

- The REPL is project-scoped and stateful.
- Top-level declarations can be reused in later calls.
- Use `resetState=true` when old declarations may conflict.
- Use unique names or reusable `var` names for iterative scripts.

## Capability Probing

- Do not assume language plugins or product APIs exist.
- Probe class availability or plugin availability before using product-specific APIs.
- Keep scripts product-neutral unless the target IDE is known.
