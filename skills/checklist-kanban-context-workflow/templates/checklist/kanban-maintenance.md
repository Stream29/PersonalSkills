# Kanban Maintenance

## Purpose

- Use `kanban/` only to record current work progress and completed task records.
- Do not treat content under `kanban/` as authorization to start or advance work.
- Start, resume, or advance a task only when the user explicitly requests it.
- Do not add speculative tasks that the user has not requested.
- Keep durable procedures and decisions in `checklist/`, executable task decomposition in `kanban/ongoing/`, and reusable findings in `shared-context/`.

## Draft

- Treat `kanban/Draft.md` as the user's writing space.
- Keep `kanban/Draft.md` read-only unless the user explicitly asks the agent to edit or promote identified content.
- Allow the user to add a standalone `---` divider as the writing completion boundary.
- Treat content before the divider as finished writing and content after it as still being written.
- Treat all draft content as still being written when no divider is present.
- Do not treat the divider as authorization to advance the completed content.
- Do not add, remove, or move the divider unless the user explicitly asks.
- Treat a request to advance an identified draft item as permission to create its ongoing task file and remove only the identified content from `kanban/Draft.md`.
- Do not edit unrelated draft content while promoting an item.

## Ongoing Tasks

- Keep each unfinished task in a separate Markdown file under `kanban/ongoing/`.
- Create or update a task file only while performing work explicitly requested by the user.
- Decompose work the agent advances into a task tree before implementing it.
- Treat task files the user is actively advancing as read-only unless the user explicitly asks the agent to edit them.
- Keep paused or blocked tasks under `kanban/ongoing/` and describe the current condition under `Details` when useful.

## Agent Updates

- Create or update the relevant ongoing task file when starting user-requested work.
- Create new ongoing task files from `kanban/ongoing/YYYY-MM-DD-title.md`.
- Update the task tree immediately whenever its decomposition or progress materially changes.
- Add newly discovered necessary work to the tree without expanding the user's requested scope.
- Finalize completed task files using `kanban/done/YYYY-MM-DD-title.md`.
- Move the task file from `kanban/ongoing/` to `kanban/done/` when every task-tree node is done and the requested outcome is achieved.
- Preserve any durable result in the appropriate checklist or shared-context file before completing the task.

## Task File Format

- Keep one task per file.
- Treat `YYYY-MM-DD-title.md` as a reusable template, not as a task.
- Name each task file `YYYY-MM-DD-title.md`.
- Keep the filename stable after creating the task.
- Keep each task file to a `Task Tree` section and a free-form `Details` section.
- Record task decomposition under `Task Tree` as a nested unordered list.
- Leave unfinished task-tree nodes unmarked.
- Prefix completed task-tree nodes with `[done]`.
- Order sibling nodes by intended execution order.
- Mark a parent node `[done]` only after all of its child nodes are done.
- Make leaf nodes concrete and verifiable.
- Write any useful task-local context under `Details` without a prescribed schema.
- Do not use checkbox markers.
- Do not rewrite or reformat unrelated task files.

## Referenced Subtasks

- Allow a task-tree node to reference another task file when a subtask is large enough to need its own task tree.
- Link an unfinished referenced subtask as `[title](../ongoing/YYYY-MM-DD-title.md)`.
- Link a completed referenced subtask as `[title](../done/YYYY-MM-DD-title.md)`.
- Keep each referenced task filename unique across `kanban/ongoing/` and `kanban/done/`.
- Mark a referencing node `[done]` only when the referenced task's root node is done.
- Keep the referenced task's decomposition in its own file instead of duplicating that subtree in the parent task.
- Update every inbound link and add the referencing node's `[done]` marker when moving a referenced task from `kanban/ongoing/` to `kanban/done/`.
- Do not complete a parent task while any referenced subtask is unfinished.
- Do not create circular task references.
