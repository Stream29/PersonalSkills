# IntelliJ Platform MCP Files Editing

Source: https://www.jetbrains.com/help/idea/mcp-server.html

Use this for file reads, file creation, text edits, formatting, editor focus, and rename refactoring.

## Reading Files

- Use `read_file` or `get_file_text_by_path` to inspect file contents through the IDE.
- Use `get_all_open_file_paths` when the user refers to current or open files.
- Use `list_directory_tree_in_folder` to inspect project structure without broad shell listing.
- Prefer targeted reads over loading large files.

## Finding Files

- Use `find_files_by_glob` for path patterns.
- Use `find_files_by_name_substring` for filename fragments.
- Narrow to relevant directories when possible.

## Creating And Editing Files

- Use `create_new_file_with_text` for new files when IDE context matters.
- Use `replace_text_in_file` for focused textual edits.
- Use semantic refactoring tools for code symbol renames.
- After edits, run `reformat_file` when IDE formatting is expected.

## Rename Refactoring

- Use `rename_refactoring` for programmatic symbols.
- Provide exact symbol name, new name, project-relative path, and `projectPath`.
- Search or inspect symbol info first when there are overloads, shadowed names, or similarly named symbols.
- Validate after rename with file problems or run configurations when references may be broad.

## Editor Coordination

- Use `open_file_in_editor` when the user needs the IDE editor focused on a file.
- Do not open every file you inspect; editor focus is user-visible state.
