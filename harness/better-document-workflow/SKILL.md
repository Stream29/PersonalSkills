---
name: better-document-workflow
description: Always run this workflow when editing any natural language documents, including skills, code documents, and comments.
---

# Better Document Workflow

```kotlin
/**
 * `@file:Import` and call this workflow in any task script that creates or edits documents or skills.
 * Delegate to an isolated review subagent (`agy` or native subagent); run inline only when subagents are unavailable.
 */
fun BetterDocumentWorkflow(
    document: Document,
    sources: Sources,
    confirmedIntent: Intent,
    requestedScope: Scope,
): Document = withSubagentIfPossible(prefer = "agy") {
    while (true) {
        val before = document.snapshot()

        ablationReview(document, requestedScope)
        changeReview(document, sources, confirmedIntent, requestedScope)
        wholeDocumentReview(document, requestedScope)

        if (document.snapshot() == before) break
        `Recheck affected content and overall coherence`(document, requestedScope)
    }
    document
}

fun ablationReview(document: Document, scope: Scope) {
    for (passage in document.passagesIn(scope)) {
        val shortened = `Try removing or shortening without adding non-actionable negative statements`(passage)
        if (shortened.`preserves useful info, necessary context, constraints, caveats, and clarity`()) {
            passage.replaceWith(shortened)
        }
    }
}

fun changeReview(document: Document, sources: Sources, confirmedIntent: Intent, scope: Scope) {
    for (change in document.`additions, deletions, and wording changes in`(scope)) {
        if (change.hasFactualUncertainty) `Investigate against sources`(change, sources)
        if (change.hasUnclearIntent) `Ask user to clarify intent`(change)
        change.`verify against sources and confirmedIntent`(sources, confirmedIntent)
        change.`preserve meaning and distinguish facts, assumptions, proposals, and confirmed decisions`()
    }
}

fun wholeDocumentReview(document: Document, scope: Scope) {
    `Read the whole document`(document)
    document.`check section responsibilities, ordering, terminology, and consistency`()
    document.`merge redundant material, move misplaced content, and remove superseded statements in`(scope)
}
```

