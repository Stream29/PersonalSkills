---
name: gradle
description: "Use when working with Gradle projects."
---

# Gradle

- Prefer `buildSrc` for reusable logic and put repeated build behavior in convention plugins.
- Always detect the running Gradle Daemon JVM and explicitly provide that JVM to `gradlew`; treat inability to reuse the available Daemon as a build failure.
- Treat Gradle commands as long-running processes and be patient.
