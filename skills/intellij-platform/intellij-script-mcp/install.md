# IntelliJ Script MCP Install

Use this when installing or configuring JetBrains IDE script MCP servers.

This covers `Stream29/IdeaKtsReplMcp`, a Kotlin script REPL MCP server for IntelliJ Platform IDEs.

Source: https://github.com/Stream29/IdeaKtsReplMcp

## What It Installs

- `IdeaKtsReplMcp` is an IntelliJ IDEA plugin.
- It exposes one MCP tool: `kotlin_eval`.
- `kotlin_eval` runs Kotlin script inside the IDE process.
- REPL state is kept per open project.
- The script receives `project` as the main IntelliJ Platform entry point.
- The tool returns the script's final expression value.
- Stdout is not the answer channel.

## Build The Plugin

Use this when installing from the source repository.

```sh
./gradlew buildPlugin
```

The installable plugin ZIP is created under:

```text
build/distributions/IdeaKtsReplMcp-<version>.zip
```

For plugin development, launch a sandbox IDE:

```sh
./gradlew runIde
```

## Install Into IntelliJ IDEA

Manual installation from disk:

- Open `Settings | Plugins`.
- Click the gear icon.
- Choose `Install Plugin from Disk...`.
- Select the ZIP from `build/distributions`.
- Restart the IDE when prompted.

After restart:

- Open any project.
- Open `Settings | Tools | IdeaKtsReplMcp`.
- Enable the MCP server if it is disabled.
- Keep the bind host on localhost unless the user intentionally wants remote access.
- Confirm the configured host and port.

Default local endpoint:

```text
http://127.0.0.1:39393/mcp
```

## Install By CLI When Available

Use the IDE launcher only when the plugin has a known plugin ID or custom repository URL.

```sh
<launcher> installPlugins <plugin-id ...> [repository-url ...]
```

Rules:

- Do not guess the Marketplace plugin ID.
- If using a custom plugin repository, pass the repository URL after the plugin ID.
- For a locally built ZIP, prefer `Install Plugin from Disk...` unless the IDE launcher supports the chosen local install flow.
- See `../intellij-platform-cli/plugins.md` for JetBrains plugin CLI details.

## Rules

- Install or enable the JetBrains IDE script MCP server from the target IDE.
- Use the exact URL or command shown by the IDE plugin or MCP server settings.
- Do not guess MCP ports, URLs, launcher names, plugin IDs, or server names.
- Use one MCP server entry per IDE when multiple JetBrains IDEs are configured.
- Choose clear server names such as `idea_script`, `webstorm_script`, `pycharm_script`, or `goland_script`.

## Configure MCP Client

Use the exact endpoint from `Settings | Tools | IdeaKtsReplMcp`.

Recommended server names:

- `idea_script` for IntelliJ IDEA.
- `webstorm_script` for WebStorm if the plugin is installed there.
- `pycharm_script` for PyCharm if the plugin is installed there.
- `goland_script` for GoLand if the plugin is installed there.

Use `http://127.0.0.1:39393/mcp` only when the IDE settings confirm the default endpoint.

## Codex

```sh
codex mcp add <name> --url <ide-script-mcp-url>
```

Equivalent config:

```toml
[mcp_servers.<name>]
url = "<ide-script-mcp-url>"
```

## OpenCode

```json
{
  "$schema": "https://opencode.ai/config.json",
  "mcp": {
    "<name>": {
      "type": "remote",
      "url": "<ide-script-mcp-url>",
      "enabled": true
    }
  }
}
```

## Claude Code

HTTP or streamable HTTP:

```sh
claude mcp add --transport http --scope user <name> <ide-script-mcp-url>
```

SSE:

```sh
claude mcp add --transport sse --scope user <name> <ide-script-mcp-url>
```

Stdio:

```sh
claude mcp add --transport stdio --scope user <name> -- <command> <args>
```

## Verify

- Restart the MCP client after adding or changing the server config.
- Confirm the client lists a tool named `kotlin_eval`.
- Run a minimal script:

```kotlin
project.name
```

- If the call fails, check:
  - The IDE is running.
  - A project is open.
  - `IdeaKtsReplMcp` is enabled.
  - The bind host and port match the MCP client config.
  - The endpoint path is `/mcp`.

## Safety

- This is unrestricted code execution inside the IDE process.
- Keep the server bound to localhost unless remote access is intentional.
- Scripts can access project files, local files, IDE services, and credentials available to IDE integrations.
- Do not expose the server to untrusted networks.
