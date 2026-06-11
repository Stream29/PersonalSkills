# Gradle Dependencies

Sources:

- https://docs.gradle.org/current/userguide/version_catalogs.html
- https://docs.gradle.org/current/userguide/declaring_dependencies.html
- https://docs.gradle.org/current/userguide/platforms.html
- https://docs.gradle.org/current/userguide/dependency_constraints_conflicts.html
- https://docs.gradle.org/current/userguide/dependency_locking.html
- https://docs.gradle.org/current/userguide/dependency_verification.html
- https://docs.gradle.org/current/userguide/dependency_resolution.html

Use this for dependency declarations, dependency graph debugging, and reproducibility.

## Version Management

- Prefer `gradle/libs.versions.toml` for shared dependency and plugin aliases.
- Use platforms or BOM imports when a family of dependencies must stay aligned.
- Use dependency constraints for library-published version guidance.
- Avoid forced versions unless weaker options cannot solve the conflict.

## Reproducibility

- Use dependency locking when dynamic versions or changing modules are intentionally allowed but builds need stable resolution.
- Use dependency verification when dependency integrity matters.
- Keep repository declarations centralized where the project already does so.

## Debugging

- Use `./gradlew dependencies --configuration <configuration>` for a configuration tree.
- Use `./gradlew dependencyInsight --dependency <module> --configuration <configuration>` for conflict reasons.
- Use `--refresh-dependencies` for stale cache diagnostics.
- Check included builds and substitution rules before assuming a module came from an external repository.
