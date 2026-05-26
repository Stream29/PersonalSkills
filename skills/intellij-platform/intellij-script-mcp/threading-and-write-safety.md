# IntelliJ Script MCP Threading And Write Safety

Use this before running `kotlin_eval` scripts that read indexes, touch PSI, mutate files, or use UI APIs.

## Read Rules

- Use `readAction` for PSI, VFS, and model reads.
- Use `smartReadAction(project)` for project-wide PSI analysis, indexes, resolve, or StubIndex access.
- Commit documents before PSI reads when editor changes matter.
- Keep read actions small.

## Write Rules

- Use `writeAction` for low-level mutations.
- Prefer `writeCommandAction(project, "Command name")` for user-visible document or PSI edits.
- Use clear command names.
- Do not mutate PSI, documents, or project model from plain background code.

## EDT Rules

- Use `withContext(Dispatchers.EDT)` only for short UI-only work.
- Prefer `Dispatchers.EDT` over generic UI dispatchers in IntelliJ Platform code.
- Do not block the EDT.
- Do not wait on long futures or latches from the EDT.

## Cancellable Work

- Prefer IntelliJ coroutine APIs.
- Avoid unbounded CPU loops.
- Avoid blocking waits that ignore interruption.
- For long tasks, start async work and poll later.

## Safety Checklist

- Does the script need smart mode?
- Does it read unsaved editor changes?
- Does it mutate state?
- Does any part need EDT?
- Can the operation run too long for one MCP call?
