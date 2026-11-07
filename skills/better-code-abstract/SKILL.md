---
name: better-code-abstract
description: Use when designing APIs, specs, schemas, and code structure.
---

# Better Code Abstract

```kotlin
enum class CodeAbstractKeyword {
    // Strategic & Boundaries
    Domain, BoundedContext, SingleResponsibility, SpecVsImplBoundary,
    Partnership, SharedKernel, CustomerSupplier, Conformist,
    AntiCorruptionLayer, OpenHostService, PublishedLanguage, SeparateWays,

    // Tactical & State/Schema
    Entity, ValueObject, Aggregate, AggregateRoot, DomainService, DomainEvent,
    Module, Repository, ApplicationService, DtoDoPo,
    SingleSourceOfTruth, FineGrainedQueryableSchema,

    // Contracts & Simplicity
    MinimalOrthogonalPrimitives, ExtensionComposition, StatelessObjectOverBuilder,
    ExplicitIntentNoArbitraryDefaults, ChannelVsRpcSymmetry,
    ZeroPassThroughIndirection, StructuredResourceLifecycle,
}

fun refineCodeAbstraction(design: CodeDesign): CodeDesign =
    design
        .`check relevant concepts without mechanical over-application`(CodeAbstractKeyword.entries)
        .`keep each file/module within its single responsibility and public contracts in the spec boundary`()
        .`expose minimal orthogonal primitives on contracts and compose business views via extensions`()
        .`delete pass-through wrappers, unmotivated builders, and arbitrary default arguments`()
```
