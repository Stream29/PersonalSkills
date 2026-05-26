# IntelliJ Platform CLI Launchers

Use this when configuring or locating JetBrains IDE command-line launchers.

Source: https://www.jetbrains.com/help/idea/working-with-the-ide-features-from-command-line.html

## Standalone Installations

- The IDE installation directory has launchers under `bin`.
- Windows commonly uses `idea64.exe` or `idea.bat`.
- Linux installations include `idea.sh` under `bin`.
- Add the IDE `bin` directory to `PATH` when the launcher should work from any shell directory.
- On Windows, installer setup can add the launchers directory to `PATH`.
- On Linux, a symlink from the IDE launcher script into a `PATH` directory is common.

Windows current-shell PATH pattern:

```bat
set PATH=%PATH%;C:\Program Files\JetBrains\IntelliJ IDEA\bin
```

Windows persistent user PATH pattern:

```bat
setx PATH "%PATH%;C:\Program Files\JetBrains\IntelliJ IDEA\bin"
```

Linux symlink pattern:

```sh
ln -s /opt/idea/bin/idea.sh /usr/local/bin/idea
```

## Toolbox

- Prefer JetBrains Toolbox generated shell scripts when Toolbox manages the IDE.
- Check Toolbox settings for the shell scripts location.
- Toolbox can generate a different shell script for each installed IDE version.
- Rename the script from the specific IDE instance settings when several versions exist.
- Common macOS locations:
  - `/usr/local/bin`
  - `~/Library/Application Support/JetBrains/Toolbox/scripts`
- Common Linux location:
  - `~/.local/share/JetBrains/Toolbox/scripts`
- Common Windows location:
  - `%LOCALAPPDATA%\JetBrains\Toolbox\scripts`
- If multiple IDE versions are installed, confirm the shell script name for the exact target IDE instance.
- Do not assume `idea`, `webstorm`, `pycharm`, or similar names exist.

## Standalone macOS Apps

- Use `open` with `-n`, `-a`, and `--args` for standalone app launchers.
- If the app is not in `/Applications`, use the full `.app` path.
- Place a custom launcher only in a directory already on `PATH`.
- Ensure the launcher is executable.

Example:

```sh
#!/bin/sh
open -na "IntelliJ IDEA.app" --args "$@"
```

Make executable:

```sh
chmod +x /usr/local/bin/idea
```

## Launcher Choice

- Use the product launcher that matches the project owner.
- Use a version-specific launcher when multiple IDE versions are installed.
- Avoid changing user PATH or Toolbox settings unless the user asks.
- If no arguments are passed, the launcher starts the IDE.
