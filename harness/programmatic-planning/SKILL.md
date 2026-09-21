---
name: programmatic-planning
description: Use when expressing, executing, or tracking task plans as pseudocode scripts.
---

# Programmatic Planning

## Task Tree Structure

- Express `Task Tree` as Kotlin script pseudocode in nested Markdown lists, with top-level logic and descriptive backtick-quoted action names.
- Accompany with a `Details` section for task context, state needed to resume, inline checks, and subtask links.

```markdown
# Task Tree

- `Review task requirements and relevant code`()
- **`Implement the requested behavior`()**
- `Run validation checks for the change`()

# Details

Task context, state needed to resume, inline checks, and subtask links.
```

## Execution State

- Bold the current executing or suspended statement in each active invocation or coroutine; concurrent branches may have multiple bold positions.
- A task completes when its script finishes successfully and its scoped child coroutines have finished.

## Control Flow Examples

- Represent standard branches and loops with Kotlin blocks:

```markdown
- `if (needsMigration()) {`
  - `Run database schema migration`()
- `} else {`
  - `Verify existing schema integrity`()
- `}`
- `for (module in modules) {`
  - `Compile and test module`(module)
- `}`
- `while (hasPendingQueue()) {`
  - `Process next message`()
- `}`
```

## Concurrency Primitives

- Use `kotlinx.coroutines` primitives for structured-concurrency semantics.
- Bold active statements across concurrent branches:

```markdown
- `coroutineScope {`
  - `val taskA = async {`
    - **`Build client artifacts`()**
  - `}`
  - `val taskB = async {`
    - **`Build server artifacts`()**
  - `}`
  - `taskA.await()`
  - `taskB.await()`
  - `launch {`
    - `Report background metrics`()
  - `}`
  - `Deploy bundled artifacts`()
- `}`
```

## Exception Handling

- Express error handling and cleanup via `try` / `catch` / `finally` blocks:

```markdown
- `try {`
  - `Acquire deployment lock`()
  - **`Apply risky database migration`()**
- `} catch (e: MigrationException) {`
  - `Rollback migration step`(e)
- `} finally {`
  - `Release deployment lock`()
- `}`
```

## Subtasks

- Keep each subtask in a standalone task document; express it as a function call and link the call name to its document in `Details`.
