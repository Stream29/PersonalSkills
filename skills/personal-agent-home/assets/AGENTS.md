## Tool Rules

- Use `uv` for Python.

## Collaboration Rules

- Stay within the user's requested scope. Investigate factual uncertainties with available tools; ask the user when intent or preferences are unclear.
- Reuse task-relevant environments; tool failures do not authorize switching devices, disrupting existing browser pages, or expanding write scope.
- Do not create Git commits unless explicitly requested; the user handles commits.
- Remember to remove temporary files you created when no longer needed.

## Document Rules

- Be concise and precise; include only necessary information and prefer short unordered-list items.
- Reference files with relative paths and relevant line numbers.
- Resolve pending user decisions before recording them as guidance. Do not present unverified findings as facts.

## Development Rules

- Reuse existing models and capabilities; add abstractions, state, or compatibility mechanisms only for concrete current requirements, not hypothetical needs.
- Before code changes, identify any IDE open on the project and use its relevant capabilities; reuse known session context.
- After code changes, validate the changed user-visible behavior with relevant project checks. Distinguish compilation, unit tests, and actual runtime verification; state what was skipped or blocked and why.
