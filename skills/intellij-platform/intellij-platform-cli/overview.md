# IntelliJ Platform CLI Overview

Sources:

- https://www.jetbrains.com/help/idea/working-with-the-ide-features-from-command-line.html
- https://www.jetbrains.com/help/idea/opening-files-from-command-line.html
- https://www.jetbrains.com/help/idea/command-line-differences-viewer.html
- https://www.jetbrains.com/help/idea/command-line-merge-tool.html
- https://www.jetbrains.com/help/idea/command-line-formatter.html
- https://www.jetbrains.com/help/idea/command-line-code-inspector.html
- https://www.jetbrains.com/help/idea/install-plugins-from-the-command-line.html

Use this as the routing page for JetBrains IDE command-line features.

## Scope

- Open files, directories, and projects.
- Open diff and merge UI.
- Run IDE code formatting.
- Run IDE inspections and write reports.
- Install plugins by plugin ID.
- Start the IDE with recovery and startup options.

## Launcher Shape

- Windows executable examples usually use `idea64.exe`.
- macOS Toolbox or custom shell scripts commonly use `idea`.
- Linux installation scripts commonly use `idea.sh` or a symlink such as `idea`.
- Replace `idea` with the actual launcher for the target IDE and installation.

## Commands

- `diff`: open the IDE diff viewer.
- `merge`: open the IDE merge dialog.
- `format`: apply IDE code style formatting.
- `inspect`: run IDE code inspections for a project.
- `installPlugins`: install Marketplace or custom-repository plugins.

## Startup Options

- `nosplash`: start without the splash screen.
- `dontReopenProjects`: start at the welcome screen instead of reopening projects.
- `disableNonBundledPlugins`: start without manually installed plugins.
- `--wait`: block until opened files are closed.

## Selection Rules

- Prefer MCP for IDE-aware operations inside an already connected IDE.
- Prefer CLI when the user asks for shell integration, automation, external tools, or recovery startup.
- Confirm the real launcher name before giving exact commands.
- Avoid broad `format` or `inspect` runs unless the user wants a large-scope operation.
