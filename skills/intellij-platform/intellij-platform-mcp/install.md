# IntelliJ Platform MCP Install

Source: https://www.jetbrains.com/help/idea/mcp-server.html

Use this when installing, enabling, or configuring the official JetBrains IntelliJ Platform MCP server.

## IDE Setup

- IntelliJ IDEA 2025.2 and later include an integrated MCP server.
- The MCP Server plugin is bundled and enabled by default.
- If MCP features are missing, check `Settings | Plugins | Installed` and enable `MCP Server`.
- Open `Settings | Tools | MCP Server` for server configuration.
- Use the exact server URL or copied client configuration shown by the IDE.
- Restart the external client after changing its MCP configuration.

## External Client Setup

- Prefer the IDE's automatic client setup when it supports the target client.
- Use manual setup only when automatic setup is unavailable or the user wants explicit config.
- The official page covers clients such as Claude Code, Claude Desktop, Cursor, Codex, VS Code, and Windsurf.
- If the IDE can open the target client's settings file, use that to verify where the config was written.

## Exposed Tools

- Manage available tools in `Settings | Tools | MCP Server | Exposed Tools`.
- Disable tools that are unnecessary for the workflow to reduce accidental tool use and prompt surface.
- Re-enable tools when a task requires a missing capability.
- Check exposed tools before assuming a tool is unavailable.

## Brave Mode

- The server can ask for confirmation before running terminal commands or run configurations.
- To allow those actions without confirmation, enable the command execution setting in `Settings | Tools | MCP Server`.
- Treat this as a trust boundary.
- Do not ask the user to enable it unless repeated confirmations are blocking an intended workflow.

## Rules

- Do not guess MCP ports, URLs, launcher names, or server names.
- Use one MCP server entry per IDE when multiple JetBrains IDEs are configured.
- Choose clear server names such as `idea`, `webstorm`, `pycharm`, `goland`, `clion`, `phpstorm`, `rider`, `rubymine`, or `datagrip`.

## Codex

```sh
codex mcp add <name> --url <ide-mcp-url>
```

Equivalent config:

```toml
[mcp_servers.<name>]
url = "<ide-mcp-url>"
```

Config file:

```text
~/.codex/config.toml
```

## OpenCode

```json
{
  "$schema": "https://opencode.ai/config.json",
  "mcp": {
    "<name>": {
      "type": "remote",
      "url": "<ide-mcp-url>",
      "enabled": true
    }
  }
}
```

Config file:

```text
~/.config/opencode/opencode.json
```

## Claude Code

HTTP or streamable HTTP:

```sh
claude mcp add --transport http --scope user <name> <ide-mcp-url>
```

SSE:

```sh
claude mcp add --transport sse --scope user <name> <ide-mcp-url>
```

Stdio:

```sh
claude mcp add --transport stdio --scope user <name> -- <command> <args>
```
