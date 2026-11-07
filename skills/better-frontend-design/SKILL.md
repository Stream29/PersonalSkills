---
name: better-frontend-design
description: Use when designing, porting, or refining frontend, Wasm, desktop UI, or visual diagrams.
---

# Better Frontend Design

```kotlin
enum class FrontendDesignKeyword {
    // Interaction & Visual Alignment
    ReferenceParity, DomainSemanticAdaptation, TypographyHierarchy, CompactSpacing,
    TreeIndentationPadding, SoftWrapNoScrollbarOverlap, SpecializedItemRendering,
    CollapsibleHistory, MarkdownPipeline, BottomBarAndContextMenus,
    LightDarkTheme, MultiScaleViewport,

    // State & Data Flow Management
    SingleSourceOfTruth, UnidirectionalDataFlow, DomainVsTransientUiState,
    NewVsActiveSessionBoundary, NonBlockingPagination, StreamingResponsiveness,

    // Verification & Comparison
    LiveRendererInspection, DiagramSubgraphDirection, MultiStateSideBySideCheck,
}

fun deliverFrontendDesign(change: UiChange, reference: ReferenceUi? = null): VerifiedUi {
    if (reference != null) {
        change.`inventory reference details and separate 1-to-1 parity from domain adaptation`(reference)
    }
    change.`check and apply relevant concerns`(FrontendDesignKeyword.entries)
    return change.`verify in live browser or renderer across themes, boundary inputs, and reference`(reference)
}
```
