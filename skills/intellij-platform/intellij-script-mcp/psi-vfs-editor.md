# IntelliJ Script MCP PSI VFS Editor

Use this for `kotlin_eval` scripts that inspect project files, PSI, documents, editors, and navigation targets.

## Common APIs

- `PsiManager`: PSI files from virtual files.
- `PsiDocumentManager`: document and PSI synchronization.
- `FilenameIndex`: project file lookup through indexes.
- `GlobalSearchScope`: search scope selection.
- `VfsUtilCore`: virtual file utilities.
- `FileEditorManager`: selected editor and opening files.
- `FileDocumentManager`: document lookup and save state.
- `OpenFileDescriptor`: navigation to files and offsets.

## Document To PSI

- Get the selected editor from `FileEditorManager`.
- Commit documents via `PsiDocumentManager`.
- Resolve the PSI file from the editor document.
- Read PSI under `readAction` or `smartReadAction`.

## PSI Navigation

- Use `PsiElement.references` and `PsiReference.resolve()` to follow references.
- Prefer `navigationElement` for source-backed navigation.
- Library symbols may resolve to attached source or decompiled PSI.
- Open resolved targets with `OpenFileDescriptor` only when the user needs the IDE focus updated.

## File Search

- Use `FilenameIndex` with a narrow `GlobalSearchScope`.
- Avoid scanning every VFS file manually in large projects.
- Use smart mode when indexes or resolve are involved.

## Editing

- Prefer document edits for straightforward text replacement.
- Prefer PSI edits for syntax-aware transformations.
- Wrap edits in `writeCommandAction`.
- Save or format separately only when the user expects persistent changes.
