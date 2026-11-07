---
name: personal-agent-home
description: Use to edit the user's personal coding agent home configuration, especially AGENTS.md rules and skills, for Codex, OpenCode, Claude Code.
---

# Personal Agent Home

Canonical global rules source: [assets/AGENTS.md](assets/AGENTS.md) (read when editing rules).

```kotlin
/** Share rules and skills via symlinks through ~/.agents, never copies. */
fun syncPersonalAgentHome(repoSkills: List<Path>, agents: List<CodingAgent>) {
    val sharedHome = "~/.agents"
    val sharedSkills = "$sharedHome/skills" // Store machine-local shared skills directly here

    symlink(target = "assets/AGENTS.md", link = "$sharedHome/AGENTS.md")
    for (skill in repoSkills) {
        symlink(target = skill, link = "$sharedSkills/${skill.name}")
    }
    `Remove broken symlinks in`(sharedSkills)

    for (agent in agents) {
        val paths = `Discover agent-specific config paths`(agent)
        symlink(target = "$sharedHome/AGENTS.md", link = paths.rulesFile)
        symlink(target = sharedSkills, link = paths.skillsDir)
    }
}
```
