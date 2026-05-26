# IntelliJ Platform MCP Inspection KTS

Source: https://www.jetbrains.com/help/idea/mcp-server.html

Use this for writing, testing, and validating custom Inspection KTS scripts through official MCP.

## API Discovery

- Use `generate_inspection_kts_api` before writing non-trivial inspections.
- Use the correct language target, such as `Java` or `Kotlin`.
- Use `wrapInTags=true` only when the downstream prompt or tool benefits from tagged API text.

## Examples And PSI

- Use inspection examples tools when you need known patterns.
- Use PSI tree tools when a rule depends on syntax shape.
- Prefer PSI-based checks for structural code issues.
- Prefer normal search for simple text patterns.

## Running A Draft

- Use `run_inspection_kts` to compile and run a draft inspection against one file.
- Provide `targetFileContent` for minimal examples when the file does not need to exist.
- Treat compilation errors separately from rule behavior.
- Keep one inspection focused on one rule.

## Validating

- Use `validate_inspection_kts` when a spec file has positive and negative examples.
- Positive examples should trigger the inspection.
- Negative examples should not trigger it.
- Add negative examples before broadening a rule.

## Reporting

- Summarize found problems by file, line, severity, and message.
- Do not paste large generated API docs into final responses.
