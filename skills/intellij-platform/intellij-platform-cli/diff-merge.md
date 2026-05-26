# IntelliJ Platform CLI Diff Merge

Use this for command-line diff and merge through JetBrains IDEs.

Diff source: https://www.jetbrains.com/help/idea/command-line-differences-viewer.html
Merge source: https://www.jetbrains.com/help/idea/command-line-merge-tool.html

## Diff

Windows syntax:

```bat
idea64.exe diff <path1> <path2> [<path3>]
```

macOS syntax:

```sh
idea diff <path1> <path2> [<path3>]
```

Linux syntax:

```sh
idea.sh diff <path1> <path2> [<path3>]
```

- Two paths compare two files.
- Three paths open a three-file comparison.
- No paths opens an empty diff viewer.
- Use this for visual comparison, not automated patch generation.

## Merge

Windows syntax:

```bat
idea64.exe merge <path1> <path2> [<base>] <output>
```

macOS syntax:

```sh
idea merge <path1> <path2> [<base>] <output>
```

Linux syntax:

```sh
idea.sh merge <path1> <path2> [<base>] <output>
```

## Merge Rules

- For three-way merge, provide two modified versions, a base revision, and an output file.
- If base is omitted, the output file contents are treated as the common origin.
- If base is omitted and output is empty, the flow is effectively a two-way merge.
- Do not choose an output path that would overwrite important content unless the user expects that.

## Examples

```sh
idea diff ~/MyProject/Readme.md ~/MyProject/Readme.md.bak
idea diff
idea merge ~/Mine/Readme.md ~/Theirs/Readme.md ~/Base/Readme.md ~/Merged/Readme.md
idea merge incoming.txt current.txt result.txt
```
