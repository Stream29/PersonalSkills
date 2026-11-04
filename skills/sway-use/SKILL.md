---
name: sway-use
description: Use Sway for isolated GUI control. It's not desktop control.
---

# Sway Use

```kotlin
fun ControlSwayGui(goal: GuiGoal) {
    `Discover or start headless, nested, or dedicated Sway session`().use { session ->
        val globals = session.`inspect Wayland globals`()
        require("zwlr_virtual_pointer_manager_v1" in globals)
        require("zwp_virtual_keyboard_manager_v1" in globals)

        while (!goal.isSatisfied()) {
            // IPC provides output/seat/workspace/focus/window metadata only, not input injection.
            val ipcMeta = session.`inspect Sway IPC metadata`()
            val baseline = session.`capture screenshot`()
            // Output, surface, window, and DOM coordinates are distinct spaces.
            val coords = `Derive Sway coordinates`(ipcMeta, baseline)

            // Keep client lifetime across full motion/click/drag sequence to preserve button state.
            session.`perform smallest native Wayland action`(coords)
            check(session.`verify via screenshot or app-visible state change`())
        }
    }
}
```


