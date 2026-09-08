---
name: user-collaboration
description: "Use when asking the user questions, preparing large Markdown proposals for review, or revising documents based on user feedback."
---

# User Collaboration

## Asking Questions

- Prefer an available structured question tool, such as `ask_user` or `request_user_input`.
- Always provide an Other branch that accepts a free-form answer outside the listed options. Use the tool's built-in Other branch when available.
- If no suitable question tool is available, ask in chat.

## Large Markdown Proposals

- When large proposal in Markdown, leave an editable approval area after every substantive section and subsection.
- Blank approval feedback means no comments.
- Use this as your template:

```markdown
FIXME:

```

- User may fill in after the `FIXME:`.
- User may manually add `FIXME` in other places.
- Agent should handle all the `FIXME` flags.