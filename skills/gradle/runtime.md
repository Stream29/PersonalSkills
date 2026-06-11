# Gradle Runtime

Sources:

- https://docs.gradle.org/current/userguide/gradle_daemon.html
- https://docs.gradle.org/current/userguide/toolchains.html
- https://docs.gradle.org/current/dsl/org.gradle.buildconfiguration.tasks.UpdateDaemonJvm.html
- https://www.jetbrains.com/help/idea/gradle-jvm-selection.html
- https://www.jetbrains.com/help/idea/gradle-settings.html

Use this first when Gradle may be run from both an IDE and the command line.

## Core Distinction

- Gradle Daemon JVM: the JVM that runs Gradle itself.
- Java toolchain: the JDK Gradle uses for compiling, testing, `javadoc`, or `java` execution tasks.
- `java { toolchain { ... } }` does not guarantee that CLI Gradle and IDE Gradle share the same daemon.

## Daemon JVM Selection

- By default, Gradle runs the daemon with the JVM that started the build, using the shell path and `JAVA_HOME`.
- `org.gradle.java.home` can specify a different JVM for the build.
- `gradle/gradle-daemon-jvm.properties` has higher priority than `JAVA_HOME` and `org.gradle.java.home`.
- IntelliJ resolves Gradle JVM for existing projects from `org.gradle.java.home`, then `JAVA_HOME`, then a compatible local JDK, unless the Gradle JVM field is explicitly configured.

## Before Running Gradle

- Check for project criteria:
  - `gradle/gradle-daemon-jvm.properties`
  - `gradle.properties`
  - root and included-build `settings.gradle(.kts)`
- Check local environment:
  - `JAVA_HOME`
  - `GRADLE_USER_HOME`
  - user-level `~/.gradle/gradle.properties`
  - IDE Gradle JVM or Gradle JVM Criteria when visible.
- Compare runtime with:
  - `./gradlew --version`
  - `./gradlew --status`

## Preferred Fixes

- For Gradle 8.8+, prefer daemon JVM criteria when the project should define the daemon JDK:
  - `./gradlew updateDaemonJvm --jvm-version=<version>`
  - Add `--jvm-vendor=<vendor>` only when vendor matters.
  - Check in `gradle/gradle-daemon-jvm.properties`.
- If daemon criteria is not appropriate, align `JAVA_HOME` with the IDE Gradle JVM for the project.
- Use project-level `org.gradle.java.home=/absolute/jdk/path` only when an exact local path is acceptable.
- Keep compile/test JDK requirements in Java toolchains, not daemon settings.

## Avoid

- Do not use `org.gradle.jvmargs` to choose the JDK; it only controls JVM arguments.
- Do not assume `java -version` equals the Gradle Daemon JVM.
- Do not stop all daemons as a first step; it can disrupt IDE builds and hides the mismatch.
- Do not mix IDE JDK fixes with build logic fixes in the same change unless both are required.

## Reporting

- State the selected daemon JVM source: daemon criteria, `org.gradle.java.home`, `JAVA_HOME`, IDE setting, or fallback.
- State whether the CLI and IDE are expected to reuse the same daemon.
- If changing files, name the exact Gradle runtime file changed and why.
