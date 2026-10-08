---
name: sway-use
description: Use Sway for isolated GUI control. It's not desktop control.
---

# Sway Use

## Technical rules

- Inspect Sway's Wayland globals before acting. Pointer input needs
  `zwlr_virtual_pointer_manager_v1`; virtual keyboard input needs
  `zwp_virtual_keyboard_manager_v1`.
- Use Sway IPC for output, seat, workspace, focus, and window metadata. IPC
  inspection does not itself inject native input.
- Prefer Sway's native Wayland path.
- Keep pointer lifetime and event ordering strong enough for a complete
  motion/click/drag sequence; short-lived clients can lose button state.
- Treat output, surface, window, and DOM coordinates as different spaces.
- Verify every action with a screenshot or an application-visible state change.

## Minimal workflow

1. Discover or start a headless, nested, or dedicated Sway session.
2. Inspect Sway IPC, Wayland globals, outputs, seats, and window metadata.
3. Verify screenshot, pointer, and keyboard capabilities.
4. Capture a baseline and derive current Sway coordinates.
5. Perform the smallest native Wayland action needed.
6. Verify the result independently and clean up on completion or mismatch.
