# IntelliJ Platform MCP Search Navigation

Source: https://www.jetbrains.com/help/idea/mcp-server.html

Use this for IDE-indexed file search, text search, regex search, symbol search, and navigation.

## Search Choice

- Use `search_symbol` for classes, methods, fields, and named program elements.
- Use `search_in_files_by_text` for exact strings, config keys, messages, and UI text.
- Use `search_in_files_by_regex` for declarations, annotations, naming patterns, or structural text.
- Use `find_files_by_glob` or `find_files_by_name_substring` before content search when the target file is identifiable.

## Scoping

- Use file masks for language-specific searches.
- Use directory filters for known modules or source roots.
- Use result limits to keep output readable.
- Retry symbol search with external symbols only when project symbols are insufficient.

## Navigation

- Use search result coordinates with `get_symbol_info` for declaration or reference details.
- Use `open_file_in_editor` only when visual focus helps the user.
- Use open-file tools when the user's request points at current editor context.

## Output

- Report enough path and line information to make the result actionable.
- Do not dump large search result sets.
- Prefer a short shortlist plus next action.
