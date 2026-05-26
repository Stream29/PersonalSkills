# IntelliJ Platform CLI Startup Options

Use this for launcher options and startup recovery.

Source: https://www.jetbrains.com/help/idea/working-with-the-ide-features-from-command-line.html

## Options

- `nosplash`: start without the splash screen.
- `dontReopenProjects`: do not reopen previous projects; show the welcome screen.
- `disableNonBundledPlugins`: start without manually installed plugins.
- `--wait`: block until opened files are closed.

## Syntax

```sh
idea nosplash
idea dontReopenProjects
idea disableNonBundledPlugins
idea --wait file.txt
```

## Recovery Use Cases

- Use `dontReopenProjects` when a previously opened project crashes the IDE.
- Use `disableNonBundledPlugins` when a manually installed plugin crashes startup.
- Use both together for conservative recovery:

```sh
<launcher> dontReopenProjects disableNonBundledPlugins
```

## Boundaries

- These options do not permanently remove plugins.
- Use IDE settings to disable or uninstall problematic plugins after successful startup.
- Do not change project files as part of startup recovery unless the user asks.
- `--wait` is mainly useful for external editor workflows and scripts that need to wait for file close.
