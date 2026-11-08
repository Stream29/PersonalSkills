---
name: context-template
description: Use when asked to initialize project context management.
---

# Context Template

```kotlin
enum class ContextComponent(val paths: List<String>, val skillRepo: String, val submodulePath: String) {
    Checklists(
        paths = listOf("checklist/"), // Project rules, SOPs, and confirmed decisions
        skillRepo = "https://github.com/Stream29/checklist-workflow-skill.git",
        submodulePath = ".agents/skills/checklist-workflow/",
    ),
    Kanban(
        paths = listOf(
            "kanban/Draft.md",      // User draft space
            "kanban/discussion/",   // Task records
            "kanban/planning/",
            "kanban/executable/",
            "kanban/active/",
            "kanban/done/",
        ),
        skillRepo = "https://github.com/Stream29/kanban-workflow-skill.git",
        submodulePath = ".agents/skills/kanban-workflow/",
    ),
    AgentScript(
        paths = emptyList(),
        skillRepo = "https://github.com/Stream29/agent-script-skill.git",
        submodulePath = ".agents/skills/agent-script/",
    ),
    Resources(
        paths = listOf("resources/"), // Reusable external resources
        skillRepo = "https://github.com/Stream29/shared-context-workflow-skill.git",
        submodulePath = ".agents/skills/shared-context-workflow/",
    ),
}

fun InitContextTemplate(
    codeRepo: GitRepo,
    selected: Set<ContextComponent>,
    useBuildWrapper: Boolean = false,
): GitRepo {
    // Use codeRepo directly by default; create a wrapper only with explicit user confirmation
    // when code must remain an independent Git repository or context cannot be managed inside it.
    val root = if (useBuildWrapper) {
        require(`Confirmed by user`())
        // Place only the selected template parts and their history in Build<ProjectName>,
        // and add the code repository as a direct child submodule.
        val wrapper = `Create Git repository for template parts and their history`("Build${codeRepo.name}")
        wrapper.addSubmodule(codeRepo, path = codeRepo.name)
        wrapper
    } else {
        codeRepo
    }

    for (component in selected) {
        `Create paths adapting to project layout and preserving existing content`(root, component.paths)
        root.addSubmodule(url = component.skillRepo, path = component.submodulePath)
    }
    return root
}
```

