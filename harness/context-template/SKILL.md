---
name: context-template
description: Use when asked to initialize project context management.
---

# Context Template

## Reference Layout

```text
<project>/
├── checklist/             # Project rules, SOPs, and confirmed decisions
├── kanban/
│   ├── Draft.md           # User draft space
│   ├── discussion/        # Task records
│   ├── planning/
│   ├── executable/
│   └── done/
└── resources/             # Reusable external resources
```

## Apply Selected Parts

- Create the selected components, adapting to the project's layout and preserving existing content.
- Add each selected component's workflow repository as a Git submodule at the corresponding path:
  - [Resources](https://github.com/Stream29/shared-context-workflow-skill.git) → `.agents/skills/shared-context-workflow/`
  - [Checklists](https://github.com/Stream29/checklist-workflow-skill.git) → `.agents/skills/checklist-workflow/`
  - [Kanban](https://github.com/Stream29/kanban-workflow-skill.git) → `.agents/skills/kanban-workflow/`
  - [Planning](https://github.com/Stream29/programmatic-planning-skill.git) → `.agents/skills/programmatic-planning/`

## Optional Build Wrapper

- Use the code repository directly by default; create a wrapper only with explicit user confirmation.
- A wrapper is useful when code must remain an independent Git repository or context cannot be managed inside it.
- For code repository `<ProjectName>`, place only the selected template parts and their history in `Build<ProjectName>` and add the code repository as a direct child submodule.
