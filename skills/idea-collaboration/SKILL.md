---
name: idea-collaboration
description: Use in JVM, Java, Kotlin, Gradle, Maven, Android, or IntelliJ IDEA based projects.
---

# IDEA Collaboration

Use this skill for JVM/Kotlin-related projects.

## IDEA MCP Setup

Ask the user to enable IDEA MCP and set it up if tools are unavailable: `idea-mcp-config.md`.

## Work Rules

- Don't use IDEA MCP tools for shell commands.
- Otherwise, prefer IDEA MCP tools.

## Gradle Rules

- Use `get_run_configurations` to find existing Gradle, test, application, or build configurations. Use `execute_run_configuration` to run them.
- If it's expected to be a long run, DON'T use IDEA MCP tools, use shell commands instead.
- - The gradle daemon from IDEA should be reused as much as possible. You should align the gradle JDK with IDEA for this.

