# IntelliJ Platform CLI Open Files Projects

Use this for opening files, directories, and projects from the command line.

Source: https://www.jetbrains.com/help/idea/opening-files-from-command-line.html

## Syntax

Windows:

```bat
idea64.exe [--line <number>] [--column <number>] <path>
```

macOS launcher:

```sh
idea [--line <number>] [--column <number>] <path>
```

Linux launcher:

```sh
idea.sh [--line <number>] [--column <number>] <path>
```

## Usage

- Pass a project directory to open a project.
- Pass a file path to open that file.
- Use `--line` to place the caret on a specific line.
- Use `--column` with `--line` when a precise caret location matters.
- Use `--wait` when the shell should block until files are closed.

Examples:

```sh
idea ~/MyProject
idea --line 42 ~/MyProject/scripts/numbers.js
idea --line 42 --column 7 ~/MyProject/scripts/numbers.js
idea --wait file.txt
```

## Notes

- Opening a standalone file usually uses LightEdit unless the file belongs to an open project or a recognized project type.
- Opening a directory with an existing project opens that project.
- Opening a directory may create IDE project metadata when it is not already a project.
- Prefer MCP `open_file_in_editor` when working inside an active MCP-controlled IDE session.
- Prefer CLI open commands when integrating with shell workflows, editors, scripts, or external tools.
