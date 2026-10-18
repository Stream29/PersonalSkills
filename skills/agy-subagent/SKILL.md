---
name: agy-subagent
description: Use agy(Antigravity CLI) as an external subagent for bounded tasks.
---

# agy Subagent

## Discover and Select

- Discover syntax with `agy --help`, and `agy help <subcommand>`.
- Resolve the requested model with `agy models` and use its exact ID.

## Run a Single Task

- Use `--mode accept-edits` and `--dangerously-skip-permissions` for YOLO permissions.

```bash
agy --model gemini-3.8-flash-medium \
  --mode accept-edits --dangerously-skip-permissions \
  --output-format json \
  -p 'Without tools or file access, review: def average(xs): return sum(xs) // len(xs). Require arithmetic mean and ValueError for empty input. Return defects, corrected code, and expected results for [1,2], [-1,0], and [].'
```

## Follow-up

Pass the captured conversation ID and the next prompt.

```bash
agy --model "$model_id" --conversation "$conversation_id" \
  --mode accept-edits --dangerously-skip-permissions \
  --output-format json \
  -p 'Bounded follow-up with explicit acceptance criteria'
```
