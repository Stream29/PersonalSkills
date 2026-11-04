---
name: gradle
description: "Use when working with Gradle projects."
---

# Gradle

```kotlin
fun RunGradle(vararg args: String): BuildResult {
    val daemonJvm = `Detect running Gradle Daemon JVM`()
        ?: throw BuildFailed("No running Gradle Daemon JVM detected")

    // Treat Gradle commands as long-running processes and wait patiently.
    val result = `Execute long-running command patiently`(
        "./gradlew",
        "-Dorg.gradle.java.home=$daemonJvm",
        *args,
    )
    if (!result.reusedDaemon) {
        throw BuildFailed("Inability to reuse available Gradle Daemon")
    }
    return result
}
```

