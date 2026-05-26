# IntelliJ Platform CLI Inspect

Use this for command-line code inspections through JetBrains IDEs.

Source: https://www.jetbrains.com/help/idea/command-line-code-inspector.html

## When To Use

- Use for offline inspection reports in CI-like or maintenance workflows.
- Use when the user explicitly wants IDE inspections from the shell.
- Do not use when a running IDE MCP inspection can answer faster.
- Ensure the project SDK is configured.
- Prefer MCP `get_file_problems` for one edited file in an open IDE project.

## Syntax

Windows:

```bat
idea64.exe inspect <project> <inspection-profile> <output> [<options>]
```

macOS application inspector script:

```sh
inspect.sh <project> <inspection-profile> <output> [<options>]
```

Linux launcher:

```sh
idea.sh inspect <project> <inspection-profile> <output> [<options>]
```

## Options

- `-changes`: inspect only local uncommitted changes.
- `-d`: inspect a specific subdirectory by full path instead of the whole project.
- `-format`: output format; valid values include `xml`, `json`, and `plain`.
- `-v`: set verbosity.
- `-v0`: default low verbosity.
- `-v1`: medium verbosity.
- `-v2`: maximum verbosity.

## Examples

```sh
inspect.sh ~/MyProject ~/MyProject/.idea/inspectionProfiles/MyProfile.xml ~/MyProject/InspectionResults -v2 -d ~/MyProject/src
idea.sh inspect ~/MyProject ~/MyProject/.idea/inspectionProfiles/MyProfile.xml ~/MyProject/InspectionResults -format json
idea.sh inspect ~/MyProject ~/MyProject/.idea/inspectionProfiles/MyProfile.xml ~/MyProject/InspectionResults -changes
```

## Profiles And Results

- Project profiles usually live under `.idea/inspectionProfiles`.
- Global profiles live under the `inspection` directory inside the IDE configuration directory.
- Results can be opened later through `Code | Analyze Code | View Offline Inspection Results`.
- Generated reports may be XML, JSON, or plain text depending on `-format`.
- Inspection profiles are XML files that define enabled inspections and their options.

## Caveats

- The command-line inspector starts an IDE instance in the background.
- It may not work when another instance of the same IDE is already running.
- Headless inspection opens the project in trusted mode.
- Inspection output can be large; summarize findings instead of pasting entire reports.
- A properly configured project SDK is required.
