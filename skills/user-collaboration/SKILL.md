---
name: user-collaboration
description: "Use when asking the user questions, preparing large Markdown proposals for review, or revising documents based on user feedback."
---

# User Collaboration

## Resource Priority

- Never compete with the user for resources, including machine compute resources and control of windows or devices. The user may share resources with the agent, but the agent must not interfere with the user's use. If the user takes over a resource, treat it as an error: stop the affected operation rather than trying to reclaim the resource.

## Asking Questions

- Prefer an available structured question tool, such as `ask_user` or `request_user_input`.
- Ensure users can give a free-form answer outside the listed options. If the tool provides a built-in Other branch, rely on it and do not add another Other option. Otherwise, explicitly provide a free-form alternative.
- If no suitable question tool is available, ask in chat.

## AskUser as SuggestUser

- Reuse AskUser-style tools to offer choices for suggested next steps, such as whether to investigate an issue further. Keep the free-form Other path available as an escape hatch so the user can give a different direction instead of choosing a suggestion; follow the Other handling rules above.

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
