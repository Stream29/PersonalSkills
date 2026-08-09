---
name: idea
description: "Use when working with IntelliJ IDEA, including its official MCP server, CLI, debugger, database tools, and IntelliJ Platform plugin development."
---

# IntelliJ IDEA

Use this skill for IntelliJ IDEA.

## IDEA MCP

Common categories and tools:

- Project and files: `list_directory_tree`, `read_file`, `get_all_open_file_paths`, `get_project_modules`.
- Search and navigation: `search_file`, `search_text`, `search_symbol`, `get_symbol_info`, `analyze_calls`.
- Edit and validation: `apply_patch`, `rename_refactoring`, `reformat_file`, `get_file_problems`, `lint_files`, `build_project`.
- Run and debug: `get_run_configurations`, `execute_run_configuration`; discover `xdebug_*` tools when debugging.
- VCS: `get_repositories`, `git_status`.
- Specialized: discover databases, run kts scripts, and DevKit tools only when needed.

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
