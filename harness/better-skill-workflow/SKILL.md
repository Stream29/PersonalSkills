---
name: better-skill-workflow
description: Use when authoring or reviewing agent skills to ensure they are properly modeled, code-first, and verified against real user scenarios.
---

# Better Skill Workflow

```kotlin
@file:Import("../agent-script/SKILL.md")

fun authorSkill(userIntent: String): Path {
    // Ground the skill in what the user actually did, not in what the workflow could be.
    // Look in ~/.gemini/antigravity*/brain/*/.system_generated/logs, ~/.codex/sessions, and kanban/done.
    val history = `Collect the user's real runs of this workflow: conversations, task scripts, finished outputs, corrections`(userIntent)
    val existing = `Find the existing skill to upgrade and the neighboring skills whose style to follow`(userIntent)
    if (existing != null) {
        // Rewrites must not regress: keep everything the current skill already does well.
        `List what the existing skill does well and which user corrections it encodes`(existing)
    }

    val model = `Model the workflow from history`(
        history,
        aspects = listOf(
            "steps, decisions, loops, and suspension points",
            "inputs and how to select them: criteria plus the user's positive and negative examples",
            "outputs: location, naming from stable source facts (e.g. publish date, not run date or batch index), state such as unread/archived",
            "side effects on sources and the outside world, e.g. remove the processed item from the queue",
            "re-runs: items already processed, partial failures",
        ),
    )
    val location = `Infer where the skill belongs: project .agents/skills, the global skill repository, or local-only`(userIntent, existing)
    // Explain the background in the message before asking.
    val confirmed = askUser("Model and location for the skill:\n$model\n$location\nIs this right?")

    val skillPath = `Write the skill`(
        confirmed,
        rules = listOf(
            "body is AgentScript; comments inside code instead of prose outside",
            "one function per case; no wrapper named after the skill; no types, parameters, or helpers the steps do not need",
            "principles and keywords for common sense; spell out only what agents get wrong",
            "constraints stay as narrow as the user stated them",
            "mark behavior that has no past run as unverified",
            "never edit the user's own text unless asked",
        ),
    )
    reviewSkill(skillPath, cases = `Pick the user's past cases that have finished outputs`(history))
    return skillPath
}

fun reviewSkill(skillPath: Path, cases: List<Case>) {
    do {
        val runs = cases.map { case ->
            // Fresh agent context that loads only this skill. Run the safe parts for real so the
            // output itself can be compared; stub only irreversible side effects and record what
            // the run would have done. Desk-check with the historical tool results only when even
            // the safe parts cannot run.
            val run = `Have a subagent run the case with the skill`(skillPath, case)
            `Compare the run with the user's finished output: content, selection, naming, location, side effects`(run, case.reference)
        }
        // Fix where runs diverge from the user's past outputs; other questions a fresh agent raises are common sense.
        `Fix the skill where the runs diverged`(skillPath, runs)
        // Ablate before asking: drop or condense each part; keep it only if runs get worse without it.
        for (part in `Sections, comments, and steps of the skill`(skillPath)) {
            if (`Runs stay equally good without the part`(part)) `Remove the part, or condense it into a keyword`(part)
        }
        val feedback = askUser("Runs compared with your past outputs, plus unverified parts:\n$runs\nDoes the skill meet your requirements?")
    } while (!feedback.accepted)
}
```
