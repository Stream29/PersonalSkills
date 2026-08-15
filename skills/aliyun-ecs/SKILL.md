---
name: aliyun-ecs
description: Work with the user's personal Aliyun ECS over SSH.
---

# Aliyun ECS

## Connection

- Connect with the local SSH alias:

```bash
ssh aliyun-ecs
```

- The alias logs in as the unprivileged user `stream` with public-key authentication.
- The alias resolves the ECS through its Tailnet MagicDNS name.
- Use `sudo` for administrative commands. Use `sudo -i` only when a root shell is necessary.
- Do not attempt direct SSH login as `root`; root SSH login is disabled.
- Do not enable password authentication or expose additional ports unless the user explicitly asks.

## Remote Environment

- OS: Alibaba Cloud Linux 3.
- Home directory: `/home/stream`.
- Public endpoint and identity-file details belong in the local SSH configuration, not in this skill.

## File Transfer

Use the SSH alias for transfers:

```bash
scp <local-path> aliyun-ecs:<remote-path>
rsync -av <local-path> aliyun-ecs:<remote-path>
```

## Safety

- Inspect before changing services, firewall rules, SSH settings, or packages.
- Preserve the verified `stream` SSH path when changing authentication or networking.
- Confirm before disruptive or billable cloud operations.
