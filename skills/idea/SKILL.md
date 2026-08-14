---
name: idea
description: "Use when working with IntelliJ IDEA, including its MCP server, CLI, debugger, database tools."
---

# IntelliJ IDEA

Use this skill for IntelliJ IDEA.

## IDEA MCP

Treat the IDE's Exposed Tools list as the source of truth. Availability depends on the IDE version, enabled plugins, and MCP settings.

Use the official toolset groups as follows:

- Analysis tools: `analyze_calls`, `build_project`, `get_file_problems`, `get_project_dependencies`, `get_project_modules`, `lint_files`.
- Code Insight tools: `get_symbol_info`.
- Debugger tools: `xdebug_control_session`, `xdebug_evaluate_expression`, `xdebug_get_debugger_status`, `xdebug_get_frame_values`, `xdebug_get_stack`, `xdebug_get_threads`, `xdebug_get_value_by_path`, `xdebug_list_breakpoints`, `xdebug_remove_breakpoint`, `xdebug_run_to_line`, `xdebug_set_breakpoint`, `xdebug_set_variable`, `xdebug_start_debugger_session`.
- Execution tools: `execute_run_configuration`, `get_run_configurations`.
- Formatting tools: `reformat_file`.
- Inspection Generator MCP Tools: `validate_inspection_kts`.
- Inspection KTS MCP tools: `generate_inspection_kts_api`, `generate_inspection_kts_examples`, `generate_psi_tree`, `run_inspection_kts`.
- Refactoring tools: `rename_refactoring`.
- Search tools: `search_file`, `search_regex`, `search_symbol`, `search_text`.
- Skill Search tools: `skill_search`.
- Universal tools: `execute_tool`.

- Prefer native agent tools for database access, file operations, patches, reads, VCS, and terminal commands. Do not use Database-specific, Patch, Read, Terminal, or VCS tools, or File tools other than `open_file_in_editor`; IDEA terminal execution also has timeout and output constraints.
- Discover additional plugin-provided toolsets only when needed.
- Use `execute_tool` for tools exposed only through router-only mode.

## IDEA CLI

Use these capability groups to decide whether the CLI fits the task before resolving exact syntax:

- Open and navigate: open projects, directories, or files; use LightEdit; select a line or column; optionally wait for the file to close.
- Compare and merge: open the IDE diff viewer with `diff` or merge dialog with `merge`.
- Code maintenance: apply IDE code style with `format` or run project inspections with `inspect`.
- Plugin management: install plugins with `installPlugins`.
- Startup and recovery: control splash display, project reopening, and non-bundled plugin loading.

- Run `idea --help` for basic commands and options.
- Run `idea --list-commands` for commands exposed by the current installation.
- Run `idea --version` before giving version-sensitive guidance.
