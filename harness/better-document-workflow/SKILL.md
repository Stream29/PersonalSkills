---
name: better-document-workflow
description: Always run this workflow when editing any natural language documents, including skills, code documents, and comments.
---

# Better Document Workflow

**This workflow is suggested to be run with a subagent.** If `agy` available, use `agy`.

- Run these checks automatically before handing off new or revised documents, including skill instructions.
- Fix issues within the requested scope, then recheck affected content and overall coherence.

## Ablation Review

- Test removing or shortening each passage; keep the change only if useful information, necessary context, constraints, caveats, and reader clarity are preserved.
- Do not add negative statements that contribute no actionable constraint or necessary clarification.

## Change Review

- Check additions, deletions, and wording changes against relevant sources and the user's confirmed intent.
- Preserve meaning and distinguish facts, assumptions, proposals, and confirmed decisions.
- Investigate factual uncertainty; ask the user when intent is unclear.

## Whole-Document Review

- Read the whole document; check section responsibilities, ordering, terminology, and consistency.
- Merge redundant material, move misplaced content, and remove superseded statements.
