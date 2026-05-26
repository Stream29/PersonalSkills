# IntelliJ Script MCP Async Jobs

Use this for long-running IDE operations in `kotlin_eval`.

## Pattern

- Start long work asynchronously.
- Store the `Job`, `Deferred`, or progress `Channel` in REPL state.
- Return a concise "started" message.
- Poll in later calls.
- Cancel stored jobs when they are no longer needed.

## When To Use

- Project-wide PSI analysis.
- Large index searches.
- Gradle sync or build actions through IDE APIs.
- Completion or intention experiments that may block.
- Any operation likely to exceed the MCP call timeout.

## Progress

- Use a `Channel<String>` for progress updates.
- Poll and drain the channel in later calls.
- Keep progress messages concise.
- Include final status separately from progress lines.

## Timeouts

- Set explicit `timeoutMs` for bounded calls.
- Avoid awaiting long work in the same call that starts it.
- Handle cancellation explicitly.
- Do not assume a timed-out call stopped pure CPU work.

## Cleanup

- Cancel jobs after success, failure, or abandonment.
- Clear cached state when it may affect later scripts.
- Use `resetState=true` if stored state becomes confusing.
