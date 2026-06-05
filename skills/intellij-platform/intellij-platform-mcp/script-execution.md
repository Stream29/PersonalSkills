# IntelliJ Platform MCP Script Execution

Source: https://www.jetbrains.com/help/idea/mcp-server.html

Use this for script-like execution through official JetBrains IntelliJ Platform MCP tools.

## Choose The Route

- Use `run_inspection_kts` for Kotlin inspection scripts that analyze Java or Kotlin code.
- Use `validate_inspection_kts` when the inspection script has positive and negative examples.
- Use `execute_terminal_command` for shell scripts, build scripts, generators, and other external commands that should run in the IDE terminal environment.
- Use `execute_run_configuration` for existing IDE run configurations or executable gutter run points.
- Use debugger expression evaluation only inside a suspended debugger session.

## Inspection KTS

- Use `generate_inspection_kts_api` before writing non-trivial scripts.
- Use `generate_inspection_kts_examples` for known templates.
- Use `generate_psi_tree` when the script depends on PSI structure.
- Keep one script focused on one inspection rule.
- Treat compilation errors separately from rule behavior.

## Terminal Scripts

- Pass `executeInShell=true` when shell expansion, user shell startup, or script semantics matter.
- Set a bounded timeout and output limit.
- Remember terminal command execution may require user confirmation unless the IDE command execution setting allows it.
- Prefer normal shell tools when IDE terminal integration is not needed.

## Run Configurations

- Call `get_run_configurations` first to discover configured runs or gutter run points.
- Use an existing run configuration when environment, classpath, SDK, or framework setup matters.
- Use a file plus line only for a returned executable run point.
- Pass launch overrides only when the selected run configuration supports them and the task requires them.

## Boundaries

- Do not treat official MCP script execution as unrestricted IDE-process Kotlin or Groovy eval.
- Do not install or configure third-party eval servers unless the user explicitly asks for that tool.
- Check `Settings | Tools | MCP Server | Exposed Tools` when a script tool appears unavailable.
