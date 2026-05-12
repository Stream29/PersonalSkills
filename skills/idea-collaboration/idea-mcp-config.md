# IDEA MCP Config

Use this only when IDEA MCP is not configured or needs repair.

Use the exact URL or command from `Settings | Tools | MCP Server`. Do not guess the port.

## Codex

Prefer:

```sh
codex mcp add idea --url <idea-mcp-url>
```

Equivalent config shape:

```toml
[mcp_servers.idea]
url = "<idea-mcp-url>"
```

Config file:

```text
~/.codex/config.toml
```

## OpenCode

Add IDEA under `mcp`:

```json
{
  "$schema": "https://opencode.ai/config.json",
  "mcp": {
    "idea": {
      "type": "remote",
      "url": "<idea-mcp-url>",
      "enabled": true
    }
  }
}
```

Global config file:

```text
~/.config/opencode/opencode.json
```

## Claude Code

For an HTTP/streamable HTTP URL:

```sh
claude mcp add --transport http --scope user idea <idea-mcp-url>
```

For an SSE URL:

```sh
claude mcp add --transport sse --scope user idea <idea-mcp-url>
```

For a Stdio command:

```sh
claude mcp add --transport stdio --scope user idea -- <command> <args>
```

Verify in Claude Code with:

```text
/mcp
```
