# IntelliJ Platform MCP Run Terminal

Source: https://www.jetbrains.com/help/idea/mcp-server.html

Use this for IDE run configurations, gutter run points, and terminal commands exposed by official MCP.

## Run Configuration Discovery

- Use `get_run_configurations` without `filePath` to list project run configurations.
- Use `get_run_configurations` with `filePath` to find executable gutter locations.
- Prefer existing run configurations when setup is non-trivial.
- Use gutter run points for focused tests, main methods, scripts, and examples.

## Execution

- Use `execute_run_configuration` with `configurationName` for existing configurations.
- Use `execute_run_configuration` with `filePath` plus `line` for temporary gutter-based execution.
- Do not combine `configurationName` with `filePath` and `line`.
- Use `waitForExit=true` for short tests or checks.
- Use `waitForExit=false` for apps, servers, or long-running processes.
- Set a bounded timeout.

## Overrides

- Only pass `programArguments`, `workingDirectory`, or `envs` when needed.
- Only pass dynamic overrides when the selected run configuration supports them.
- Omit empty or null overrides to preserve configured values.
- Use whitespace-only string overrides only when intentionally clearing an existing value for one launch.

## Terminal Commands

- Use IDE terminal command tools only when the user needs terminal integration through the IDE.
- Prefer normal shell tools for ordinary shell commands.
- Avoid long-running terminal commands through MCP unless the user wants that IDE terminal session.

## Output Handling

- Check exit code when available.
- If timeout expires, remember the process may still be running.
- Use full output paths when output snapshots are truncated.
- Report exit code, timeout status, and the most relevant output lines.
