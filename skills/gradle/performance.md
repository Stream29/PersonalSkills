# Gradle Performance

Sources:

- https://docs.gradle.org/current/userguide/performance.html
- https://docs.gradle.org/current/userguide/configuration_cache.html
- https://docs.gradle.org/current/userguide/build_cache.html
- https://docs.gradle.org/current/userguide/gradle_daemon.html

Use this for slow builds, cache behavior, configuration time, and CI performance.

## Workflow

- Measure a baseline before changing settings.
- Identify whether the bottleneck is initialization, configuration, dependency resolution, or task execution.
- Apply one optimization at a time.
- Re-run the same task set when comparing results.

## Diagnostics

- Use `./gradlew <task> --profile` for local timing reports.
- Use `./gradlew <task> --scan` only when allowed by project policy.
- Use `./gradlew --status` to check daemon reuse and stale daemons.
- Inspect daemon JVM alignment before treating multiple daemons as a pure performance issue.

## Caches

- Enable build cache with `org.gradle.caching=true` when task outputs are cacheable and the project is ready.
- Enable configuration cache with `org.gradle.configuration-cache=true` when build logic and plugins are compatible.
- Treat configuration cache failures as build logic issues, not as reasons to blindly disable the feature.

## CI

- Prefer the wrapper and fixed Gradle/JDK inputs.
- Separate dependency cache, Gradle user home cache, and build output cache decisions.
- Avoid persisting machine-local daemon state across unrelated CI jobs.
