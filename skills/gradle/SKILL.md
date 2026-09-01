---
name: gradle
description: "Use when working with Gradle projects."
---

# Gradle

Use this skill for Gradle build work.

## Best Practices

- Use version catalogs for shared dependency and plugin aliases.
- Centralize repositories in `pluginManagement` and `dependencyResolutionManagement`.
- Use the Foojay toolchain resolver convention when the build should provision JDKs automatically.
- Prefer `buildSrc` for reusable logic and put repeated build behavior in convention plugins.
- Enable the build cache and configuration cache when the project and plugins are compatible.
- Reuse the available Gradle Daemon JVM when possible. Treat unreusable Gradle Daemon as a build failure.
- Always detect the running Gradle Daemon JVM and explicitly provide that JVM to `gradlew` to prevent Gradle Daemon JVM mismatches.
- Treat Gradle commands as long-running processes and be patient.
