---
name: google-flow
description: Use Google Flow (flow.google.com) via browser for AI image/video generation, editing, Scenebuilder timeline assembly, Flow Agent orchestration, and custom tools.
---

# Google Flow

```kotlin
// No official public CLI/API; drive https://flow.google.com/ in a Chromium browser via chrome-devtools MCP.
// Requires 18+ Google account in a supported region (matching Google Payments Profile; VPNs not supported).
// Always close open dropdown menus (Settings, Download media, Select model) before clicking outside—open menus swallow the first outside click.

fun openFlowStudio(): FlowProject {
    val page = `Select or open https://flow.google.com/ in Chromium`()
    // Home header also links to `Flow Music` (flowmusic.app) and `Flow TV` (labs.google/flow/tv) (unverified).
    // Check `Account details` for Flow credit pool (e.g., Ultra 20x: 25,000/mo + 50/day), AI credits, and `Visible watermarking` toggle.
    `Verify account credits and watermark setting`(page)
    return `Click "New project" or open an existing project`(page)
}

fun generateOrEditAsset(project: FlowProject, prompt: String, kind: AssetKind): Asset {
    // Top-right `Settings` controls `Grid`/`Batch` view, `S`/`M`/`L` tile size, `Sound on hover`, and `Return silent videos` toggle.
    // Ensure the bottom `Flow Agent` spark switch is OFF for direct generation controls (`Settings trigger`).
    `Turn off Flow Agent if pressed`(project)
    when (kind) {
        AssetKind.Image -> {
            // Models: Nano Banana 2.1 (Thinking: Low/Medium/High), Nano Banana 2 Lite, Nano Banana Pro; 0 credits on Ultra 20x.
            `Select Image mode, aspect ratio (16:9..9:16), model, and batch (x1..x4)`()
        }
        AssetKind.Video -> {
            // Models: Omni 1.2 Flash, Veo 3.1 (Lite / Lite [Lower Priority] / Fast / Quality).
            // Prototype with `x1` before scaling to `x2..x4` to conserve credits (e.g., x1 8s = 10 credits).
            `Select Video mode, x1, resolution (360p/720p), and duration (4s/6s/8s)`()
            // `Ingredients` anchors characters/styles across projects; `Frames` controls start/end frames (unverified).
            `Attach Ingredients via "Add ingredients to the prompt box" if needed`()
        }
    }
    `Fill prompt and click "Start generation"`(prompt)
    val asset = `Wait for generation percentage to finish`()

    // Grid tile hover `More options` is non-interactive until hovered; click the tile directly to open `/edit/<id>`.
    val editor = `Click asset tile to open Image Editor`()
    if (`needs refinement`) {
        // Also supports `Crop` menu inside Image Editor (unverified).
        `Fill "What do you want to change?" and submit`(editor) // preserves full History versions
    }
    // `Download media` offers `1K Original size`, `2K Upscaled`, `4K Upscaled` (Ultra perk).
    return `Export or click "Done editing"`(editor)
}

fun manageProjectAssets(project: FlowProject, query: String) {
    // Top `Search` matches exact names/prompts first, then visually/semantically similar image/video content; combine with `Filtering and sorting options`.
    `Search or filter by All media / Images / Videos / Characters / Scenes / Trash`(project, query)
    // `Add media menu` -> `Upload`, `New collection`, `Create character` (unverified), or `New scene`.
    `Create character or organize assets into Library collections`(project)
}

fun buildSceneTimeline(project: FlowProject, clips: List<VideoClip>): SceneVideo {
    // Open Scenebuilder (`/scene/<id>`) from `Add media menu` -> `New scene`.
    val scene = `Create new scene from Add media menu`(project)
    for (clip in clips) {
        `Click "Add clip" and select video or upload media`(scene, clip)
    }
    // Timeline supports `Save frame` (extract still), `Toggle aspect ratio`, and inline editing (`Describe how to edit this video…` with Omni 1.2 Flash).
    `Optionally edit clips inline or save frames`(scene)
    `Click "Download scene" to export stitched video`(scene) // timeline arrangement itself costs 0 credits
    return `Click "Done editing scene"`(scene)
}

fun orchestrateWithAgentAndTools(project: FlowProject, goal: String) {
    // Flip `Flow Agent` ON (bottom spark or side panel) to brainstorm shots, batch-generate, or organize `Library` collections.
    `Turn on Flow Agent and submit goal`(project, goal)
    // `/tools` hosts Community tools (e.g., Character Arc, Pocket Studio, Mondo Sónico, SwissFlow Studio).
    // `/create-tool` builds custom tools from natural language (`Voice over`, `Style morph`, `Image filter`); 0 credits (execution unverified).
    `Browse /tools or build custom tools in /create-tool`(project)
}
```
