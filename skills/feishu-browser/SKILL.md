---
name: feishu-browser
description: Use Feishu/Lark through browser
---

# Feishu Browser

- Entry points: Web Messenger and search, Documents, Knowledge AI, Minutes.
- Account caveat: the user may have multiple employers' Feishu accounts with valid logins but different permissions.

```kotlin
/** Browser doc editing is error-prone; prefer editing local Markdown and uploading. */
fun updateFeishuDocFromMarkdown(localMarkdown: MarkdownFile, targetDoc: FeishuDoc) {
    `Verify logged-in employer account matches targetDoc`()
    `Edit local markdown file`(localMarkdown)
    `Upload markdown to Feishu`(localMarkdown, targetDoc)
    `Reconstruct Mermaid diagrams as native Feishu diagrams`(targetDoc)
    `Fix corrupted formatting such as code blocks`(targetDoc)
}
```


