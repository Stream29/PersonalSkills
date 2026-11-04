---
name: agy-subagent
description: Use agy(Antigravity CLI) as an external subagent for bounded tasks.
---

# agy Subagent

Discover CLI syntax with `agy --help` and `agy help <subcommand>` when needed.

```kotlin
/**
 * Run a bounded task with explicit acceptance criteria.
 * Pass captured [conversationId] for follow-up turns.
 */
fun runAgySubagent(
    prompt: String,
    model: String = "gemini-3.8-flash-medium",
    conversationId: String? = null,
): JsonResult {
    val modelId = `Resolve exact model ID from`(sh("agy models"), model)
    val convFlag = if (conversationId != null) "--conversation \"$conversationId\" " else ""
    return sh(
        """
        agy --model "$modelId" $convFlag\
          --mode accept-edits --dangerously-skip-permissions \
          --output-format json \
          -p '$prompt'
        """.trimIndent()
    ).parseJson()
}
```


