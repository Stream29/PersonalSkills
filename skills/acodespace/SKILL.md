---
name: acodespace
description: Use when working with the user's ~/ACodeSpace workspace on any device, for code projects and development envs.
---

# ACodeSpace

```kotlin
/** Consistent coding workspace root on every device. */
public data object ACodeSpace {
    val root = "~/ACodeSpace"

    val push = "$root/push"   // Primary pushable repositories
    val local = "$root/local" // Local-only repositories
    val fork = "$root/fork"   // Forks of upstream projects
    val demo = "$root/demo"   // Demo and experiment repositories

    // Includeing LLM API keys
    fun sharedDevEnvFile(name: String) = "$root/$name.env"
}
```

