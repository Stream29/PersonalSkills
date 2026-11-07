---
name: ask-user
description: Use when asking questions or suggesting next steps.
---

# Ask User

```kotlin
/** Use for both clarifying questions and offering choices for suggested next steps. */
fun askUser(questions: List<Question>): UserAnswer {
    `Ensure the background, context, and any referenced proposals are already fully explained in the assistant message`()

    val tool = `Find available structured question tool (e.g. ask_question, request_user_input, ask_user)`()
    return if (tool != null) {
        // Rely on the tool's built-in Other branch for free-form input without duplicating it;
        // add an explicit free-form option only when the tool has no built-in Other branch.
        tool.invoke(questions)
    } else {
        `Ask in chat allowing free-form answers`(questions)
    }
}
```
