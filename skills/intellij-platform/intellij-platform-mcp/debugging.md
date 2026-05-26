# IntelliJ Platform MCP Debugging

Source: https://www.jetbrains.com/help/idea/mcp-server.html

Use this for debugger sessions, breakpoints, stepping, variable inspection, and tracepoints exposed by official MCP.

## Breakpoints

- Use debugger tools only for active debugging tasks.
- Set line breakpoints with project-relative `filePath` and 1-based `line`.
- Use `breakpointId` only for existing breakpoints returned by MCP.
- Inspect returned line text to confirm placement.
- Use temporary breakpoints for one-shot probes.
- Remove agent-owned breakpoints when they are no longer needed.

## Conditions And Tracepoints

- Add conditions only when the expression is valid in that debug context.
- Remember condition errors may appear asynchronously.
- Use non-suspending log breakpoints or tracepoints when observing flow is enough.
- Use stack logging sparingly because it can generate large output.

## Sessions

- Start a debugger session through run configuration or available debug launch tools.
- Use stepping and variable tools only after execution is suspended.
- Drain breakpoint or tracepoint events when available.
- Do not leave background debug sessions running without telling the user.

## Cleanup

- Verify active breakpoints before and after cleanup.
- Remove by `breakpointId` when possible.
- Remove by file and line when the id is unavailable.
- Do not remove user-owned breakpoints unless explicitly requested.
