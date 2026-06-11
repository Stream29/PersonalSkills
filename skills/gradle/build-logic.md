# Gradle Build Logic

Sources:

- https://docs.gradle.org/current/userguide/plugins.html
- https://docs.gradle.org/current/userguide/java_gradle_plugin.html
- https://docs.gradle.org/current/userguide/best_practices_structuring_builds.html
- https://docs.gradle.org/current/userguide/sharing_build_logic_between_subprojects.html

Use this for convention plugins, custom tasks, and reusable build behavior.

## Convention Plugins

- Use convention plugins to centralize repeated build configuration.
- Prefer precompiled script plugins for concise declarative conventions.
- Prefer binary plugins when behavior needs reusable types, services, task classes, or tests.
- Keep plugin IDs stable and domain-specific.

## Location

- Prefer `build-logic` as an included build for modern shared build logic.
- Keep using `buildSrc` when the project already uses it and migration is outside the task.
- Do not introduce a new build-logic layer for a one-off setting.

## Plugin Development

- Apply `java-gradle-plugin` for Gradle plugin projects.
- Use TestKit for functional plugin tests when plugin behavior changes.
- Define task inputs and outputs with Gradle property annotations.
- Avoid eager task realization; prefer `tasks.register` and lazy providers.

## Safety

- Do not move build logic between `buildSrc` and `build-logic` without validating IDE import and CLI builds.
- Do not put environment-specific paths in convention plugins.
- Keep Android-specific build logic separate from generic JVM build logic unless the project already combines them.
