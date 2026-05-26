# IntelliJ Platform CLI Plugins

Use this for installing JetBrains IDE plugins from the command line.

Source: https://www.jetbrains.com/help/idea/install-plugins-from-the-command-line.html

## Marketplace Plugins

Windows:

```bat
idea64.exe installPlugins <plugin-id ...> [repository-url ...]
```

macOS:

```sh
idea installPlugins <plugin-id ...> [repository-url ...]
```

Linux:

```sh
idea.sh installPlugins <plugin-id ...> [repository-url ...]
```

## Examples

Marketplace plugin:

```sh
idea installPlugins org.jetbrains.plugins.github
```

Custom repository:

```sh
idea installPlugins com.example.myplugin http://plugins.example.com:8080/updatePlugins.xml
```

## JAR Plugins On macOS

Copy the JAR into the IDE plugins directory and restart the IDE:

```sh
cp plugin.jar ~/Library/Application\ Support/JetBrains/<Product><Version>/plugins/
```

Other platform JAR plugin directories:

```bat
copy plugin.jar %APPDATA%\JetBrains\Roaming\<Product><Version>\plugins\
```

```sh
cp plugin.jar ~/.local/share/JetBrains/<Product><Version>/plugins/
```

## Rules

- Do not guess plugin IDs.
- Public Marketplace plugin IDs are shown on plugin pages under additional information.
- Plugin IDs are declared in `plugin.xml`.
- Restart the IDE after installing plugins when required.
- Installing plugins into a fresh IDE settings directory can affect first-launch settings import behavior.
- Installing a plugin means writing it into the IDE plugins directory.
