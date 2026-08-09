---
name: kodex-home
description: Inspect the local Kodex home, including sessions, settings, logs, credentials, and generated artifacts.
---

# Kodex Home

Inspect Kodex-owned data directly in `~/.kodex/`.

## Home contents

```text
~/.kodex/
├── auth.yml
├── generated_images/<session-id>/<call-id>.png
├── log/Kodex.log
├── sessions/
└── settings.yml
```

- `auth.yml`: Optional Kodex-owned credentials. Treat it as secret and do not expose its contents.
- `generated_images/`: Generated image artifacts grouped by sanitized session ID.
- `log/`: Rolling Kodex application logs for diagnostics.
- `sessions/`: Filesystem-backed root sessions and nested subagents.
- `settings.yml`: Sparse Kodex global overrides, including Codex Home, auth source, shell, input, new-session, title, MCP, and hook settings.

## Session layout

```text
~/.kodex/sessions/<root-index>/
├── compaction/<index>.json
├── settings/<index>.json
├── stable/<index>.json
├── subagents/<child-index>/...
├── timestamp/<index>.json
├── token-count/<index>.json
├── unstable/<index>.json
└── lock.json
```

- Root and child names are non-negative integer indexes.
- Map each selector segment after the root through `subagents/<index>`.

## Sparse timelines

- Every timeline stores change points as `<index>.json`.
- Indexes are sparse and shared across timelines.
- The value visible at index `N` is the greatest stored index not exceeding `N`.

Timeline meanings:

- `settings`: Model, `cwd`, `threadName`, and other agent settings.
- `timestamp`: Activity time used to annotate events and order sessions by recency.
- `stable`: Canonical completed history. Each stored file contains one serialized event with a `type`.
- `unstable`: Pending-event snapshots. Only the latest visible snapshot matters; never report it as completed.
- `compaction`: Checkpoints defining the model-visible compacted prefix. Raw stable history remains available.
- `token-count`: Token-count snapshots.

Use the latest visible `settings` value for session metadata and the latest `timestamp` value for last activity. Associate a stable event with the timestamp visible at that event's index.

## Event schemas

- Message, reasoning, content-item, and hosted-tool payloads largely follow current OpenAI Responses API models.
