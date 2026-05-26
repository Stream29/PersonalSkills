# IntelliJ Platform CLI Format

Use this for command-line code formatting through JetBrains IDEs.

Source: https://www.jetbrains.com/help/idea/command-line-formatter.html

## When To Use

- Use for automated formatting outside a running IDE session.
- Use for large maintenance formatting when IDE code style is the source of truth.
- Do not use when preserving unsaved editor state matters.
- Do not use when another IDE instance prevents the command-line formatter from running.
- Prefer MCP `reformat_file` for one or a few files in an already open IDE project.

## Syntax

Windows launcher:

```bat
idea64.exe format [<options>] <path ...>
```

macOS application formatter script:

```sh
./format.sh [<options>] <path ...>
```

Linux launcher:

```sh
idea.sh format [<options>] <path ...>
```

## Options

- `-h`: show help.
- `-m` or `-mask`: comma-separated file masks; supports `*` and `?`.
- `-r` or `-R`: process directories recursively.
- `-s` or `-settings`: code style settings file.
- `-allowDefaults`: use default code style when no project or settings file applies.
- `-charset`: preserve encoding and enforce a charset such as `ISO-8859-15`.
- `-d` or `-dry`: validate formatting in memory and return non-zero if files differ.

## Settings Resolution

- `-s` can point to exported code style settings.
- Older projects may use `.idea/codeStyleSettings.xml`.
- Modern projects may use `.idea/codeStyles/Project.xml`.
- EditorConfig files in parent directories are also applied.
- EditorConfig settings override overlapping IDE code style settings.
- If no settings file, project settings, or `-allowDefaults` apply, files may be ignored.

## Examples

```sh
idea.sh format -allowDefaults ~/Data/src/hello.html ~/Data/src/world.html
idea.sh format -allowDefaults -r ~/Data/src
idea.sh format -s ~/Data/settings.xml -m '*.xml,*.html' ~/Data/src
idea.sh format -dry -r src
```

## Notes

- The formatter applies IDE code style and EditorConfig where applicable.
- Required language plugins must be installed and enabled.
- If no settings apply and `-allowDefaults` is not used, files may be skipped.
- Dry-run mode is useful before applying large formatting changes.
- The command-line formatter launches a background IDE instance.
- It may not work while another instance of the same IDE is already running.
