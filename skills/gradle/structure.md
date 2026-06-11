# Gradle Structure

Sources:

- https://docs.gradle.org/current/userguide/multi_project_builds.html
- https://docs.gradle.org/current/userguide/composite_builds.html
- https://docs.gradle.org/current/userguide/best_practices_structuring_builds.html
- https://docs.gradle.org/current/userguide/organizing_gradle_projects.html

Use this for project layout, included builds, and shared build logic placement.

## Key Files

- `settings.gradle.kts` or `settings.gradle`: build name, included projects, plugin management, and included builds.
- `build.gradle.kts` or `build.gradle`: project build logic.
- `gradle.properties`: Gradle properties and project-wide build flags.
- `gradle/libs.versions.toml`: standard version catalog location.
- `gradle/wrapper/gradle-wrapper.properties`: wrapper distribution version.

## Layout Rules

- Prefer Kotlin DSL for new build scripts unless the project already standardizes on Groovy DSL.
- Keep source files out of the root project unless the root project is intentionally buildable.
- Use explicit `include(...)` entries and avoid accidentally creating empty projects.
- Use `pluginManagement` and `dependencyResolutionManagement` in settings for centralized repositories.

## Shared Build Logic

- Prefer an included `build-logic` composite build for reusable build logic in modern builds.
- Use `buildSrc` when the existing project already depends on it and the change is narrow.
- Keep repeated subproject configuration in convention plugins rather than copy-pasting `subprojects { ... }` blocks.
