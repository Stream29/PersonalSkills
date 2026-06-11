# Gradle CLI

Sources:

- https://docs.gradle.org/current/userguide/command_line_interface.html
- https://docs.gradle.org/current/userguide/gradle_wrapper.html
- https://docs.gradle.org/current/userguide/command_line_interface_basics.html

Use wrapper-first commands unless the task is creating or repairing a wrapper.

## Discovery

- Use `./gradlew tasks` to discover available tasks.
- Use `./gradlew help --task <task>` before assuming task options.
- Use `./gradlew projects` for multi-project task paths.
- Prefer fully qualified task paths in large builds, such as `:app:test`.

## Execution

- Run the smallest task that validates the change.
- Use `--continue` only when collecting multiple failures matters.
- Use `--info` for actionable diagnostic detail; reserve `--debug` for deeper Gradle internals.
- Use `--scan` only when the user accepts publishing or the project policy allows it.

## Common Flags

- `-p <dir>`: run with a different project directory.
- `-x <task>`: exclude a task deliberately.
- `--tests <pattern>`: filter JVM tests.
- `--rerun-tasks`: ignore up-to-date checks for a diagnostic run.
- `--offline`: verify cached dependency behavior.
- `--refresh-dependencies`: refresh dependency resolution caches.

## Wrapper Rules

- Prefer `./gradlew` over a globally installed `gradle`.
- Inspect `gradle/wrapper/gradle-wrapper.properties` before changing wrapper behavior.
- Use the wrapper task for upgrades, then run the wrapper once again if scripts need regeneration.
