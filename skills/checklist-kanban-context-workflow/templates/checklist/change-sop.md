# Change SOP

## Before Changing Files

- Check shared context, checklists, and relevant kanban task files.
- Ask the user directly if a required decision is uncertain.
- Identify the smallest relevant file set.
- Read nearby code before editing to keep the style consistency.

## While Changing Files

- Follow the active kanban task tree when one exists.
- Keep implementation changes scoped to the user's request.
- Follow existing project patterns once they exist.
- Add abstractions only when they remove real complexity.
- Do not edit generated files unless the task requires it.
- Do not revert user changes.

## After Changing Files

- Remove temporary files.
- Run the relevant validation checklist.
- Report checks that were run and checks that were not applicable.
