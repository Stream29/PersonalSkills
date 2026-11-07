---
name: better-natural-language-workflow
description: Use when creating, editing, or reviewing any natural language text, including human-facing replies, comments, explanations, docs, and AI-facing skills, rules, prompts, or task scripts.
---

# Better Natural Language Workflow

Compose the relevant functions below based on the target audience and task scenario.

```kotlin
/** For text read by humans (replies, PR comments, explanations, docs). */
fun refineForHuman(text: NaturalLanguageText, reader: HumanReader): NaturalLanguageText {
    val knownContext = `Identify what reader already knows or sees in their immediate context`(reader, text)
    val concerns = `Sort out reader's actual focus, questions, and decision points`(reader, text)

    text.`remove redundant narration of knownContext`(knownContext)
    text.`structure and focus response around concerns`(concerns)
    return text
}

/** For text read by AI agents (skills, AGENTS.md rules, prompts, task scripts). */
fun refineForAi(text: NaturalLanguageText, agent: TargetAgent): NaturalLanguageText {
    val trajectory = `Consider agent's actual execution trajectory, tool habits, and failure modes`(agent, text)
    text.`verify and adjust text so agent can work effectively from it without guessing or skipping steps`(trajectory)
    return text
}

/** Remove bloat while keeping all useful information and constraints. */
fun ablateText(text: NaturalLanguageText, scope: Scope = text.fullScope) {
    for (passage in text.passagesIn(scope)) {
        val shortened = `Try removing or shortening without adding non-actionable negative statements`(passage)
        if (shortened.`preserves useful info, necessary context, constraints, caveats, and clarity`()) {
            passage.replaceWith(shortened)
        }
    }
}

/** Verify factual accuracy and intent alignment of edits against sources. */
fun reviewChanges(text: NaturalLanguageText, sources: Sources, confirmedIntent: Intent, scope: Scope = text.fullScope) {
    for (change in text.`additions, deletions, and wording changes in`(scope)) {
        if (change.hasFactualUncertainty) `Investigate against sources`(change, sources)
        if (change.hasUnclearIntent) `Ask user to clarify intent`(change)
        change.`verify against sources and confirmedIntent`(sources, confirmedIntent)
        change.`preserve meaning and distinguish facts, assumptions, proposals, and confirmed decisions`()
    }
}

/** Check global structure, terminology, and coherence across the whole document. */
fun reviewWholeText(text: NaturalLanguageText, scope: Scope = text.fullScope) {
    `Read the whole text`(text)
    text.`check section responsibilities, ordering, terminology, and consistency`()
    text.`merge redundant material, move misplaced content, and remove superseded statements in`(scope)
}

/** Run a multi-pass review until convergence, delegating to an isolated subagent when available. */
fun convergeTextReview(
    text: NaturalLanguageText,
    reviewPass: (NaturalLanguageText) -> Unit,
): NaturalLanguageText = withSubagentIfPossible(prefer = "agy") {
    while (true) {
        val before = text.snapshot()
        reviewPass(text)
        if (text.snapshot() == before) break
        `Recheck affected content and overall coherence`(text)
    }
    text
}
```
