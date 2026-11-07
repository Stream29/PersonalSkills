---
name: ide-collaboration
description: Use when working on code projects.
---

# IDE Collaboration

```kotlin
fun collaborateWithIde(project: Project) {
    val ide = `Identify open IDE on project or reuse known session context`(project) ?: return

    `Use relevant IDE capabilities during inspection and code changes`(ide)
    if (`Created or modified files for the user to inspect or review`()) {
        ide.`open files in editor for user`(targetFiles)
    }
}
```
