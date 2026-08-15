---
name: xiaoxin-ubuntu
description: Work with the user's Xiaoxin Ubuntu device over SSH.
---

# Xiaoxin Ubuntu

## Connection

```bash
ssh xiaoxin-ubuntu
```

## Lid-Closed Operation

- GNOME Caffeine keeps the device awake while it acts as a closed-lid server.
- After a reboot, the user must log in to the graphical session once before Caffeine restores its inhibitor.
- Avoid a remote reboot unless that graphical login can be completed.
