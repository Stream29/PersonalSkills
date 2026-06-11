---
name: gradle
description: "Use when working with Gradle builds, Gradle Wrapper, Gradle Daemon JVM/toolchain alignment, IntelliJ or Android Studio vs CLI Gradle JVM mismatches, dependency management, version catalogs, convention plugins, multi-project builds, performance, configuration cache, build cache, or troubleshooting Gradle commands."
---

# Gradle

Use this skill for Gradle build work.

## Index

- `runtime.md`: Gradle Daemon JVM, IDE-vs-CLI JDK mismatches, Java toolchains, and safe diagnostics.
- `cli.md`: wrapper-first command usage, task discovery, focused execution, and common flags.
- `structure.md`: settings files, multi-project builds, composite builds, and `build-logic`.
- `dependencies.md`: version catalogs, platforms, constraints, locking, verification, and resolution debugging.
- `build-logic.md`: convention plugins, `buildSrc`, included build logic, and plugin development.
- `performance.md`: build scans, profiling, configuration cache, build cache, and CI performance checks.

## Boundaries

- Prefer the project wrapper: `./gradlew` on Unix-like systems and `gradlew.bat` on Windows.
- Read `runtime.md` before running Gradle when an IDE is open, JDK selection is unclear, or daemon reuse matters.
- Separate the JVM that runs Gradle from Java toolchains that compile or test project code.
- Do not run `./gradlew --stop` unless the user asked to stop daemons or daemon state is the problem.
- Do not guess JDK paths, Gradle JVM settings, wrapper versions, or IDE ownership.
