---
name: document-review-workflow
description: Use when a document requires review by the user.
---

# Document Review Workflow

```kotlin
/** Apply only when confirmed by the user. */
fun DocumentReviewWorkflow(
    document: Document,
    reviewFocus: String,
): MarkdownFile {
    require(`Confirmed by user`())
    var file = `Put document in editable Markdown file`(document)

    if (file.isLarge) {
        for (section in file.`substantive sections and subsections`()) {
            section.appendFeedbackArea(
                """
                FIXME:

                """.trimIndent()
            )
        }
    }

    do {
        `Share relative path, relevant line numbers, and reviewFocus with user`(file, reviewFocus)
        `Wait for user review in file`() // suspension

        file = `Reread current document preserving user edits`(file)
        for (fixme in file.`find all FIXME markers`()) {
            if (fixme.feedback.isBlank()) {
                fixme.`remove marker (blank feedback means no comments)`()
            } else {
                `Revise affected content preserving user edits`(file, fixme)
            }
        }
        `Summarize changes and remaining review points`(file)
    } while (file.`has remaining review points or FIXME markers`())

    return file
}
```

