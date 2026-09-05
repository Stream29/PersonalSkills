---
name: aliyun-ecs
description: Work with the user's personal Aliyun ECS over SSH.
---

# Aliyun ECS

## Connection

- Connect with `ssh aliyun-ecs`.
- Do not attempt direct SSH login as `root`; root SSH login is disabled.
- Public endpoint and identity-file details belong in the local SSH configuration, not in this skill.

## Safety

- Do not enable password authentication or expose additional ports unless the user explicitly asks.
- Preserve the working SSH connection path when changing authentication or networking.
- Confirm before disruptive or billable cloud operations.
