---
name: better-code-abstract
description: Use when designing APIs and code structure
---

# Better Code Abstract

Use the following DDD techniques as needed to improve cohesion and reduce coupling. Do not adopt all of them or apply them mechanically.

## Strategic Modeling

- **Domain**: Model the problem space and the solution space in business terms.
- **Bounded Context**: Define an explicit semantic and responsibility boundary for a domain model.
- **Context Map**: Describe the relationships and integration patterns between bounded contexts.
  - Partnership
  - Shared Kernel
  - Customer–Supplier
  - Conformist
  - Anti-corruption Layer
  - Open Host Service
  - Published Language
  - Separate Ways

## Tactical Modeling

- **Entity**: An object distinguished by a unique identity, with a lifecycle and identity-dependent behavior.
- **Value Object**: An object defined by its attributes rather than an identity; usually immutable, value-comparable, and replaceable as a whole.
- **Aggregate**: A consistency boundary containing a group of related objects.
- **Aggregate Root**: The only entry point for external access to and modification of an aggregate.
- **Domain Service**: Domain behavior that does not naturally belong to a specific entity or value object.
- **Domain Event**: A model of a significant fact that has occurred in the domain.
- **Module**: A code-level boundary representing a bounded context or another stable business boundary.

## Engineering Implementation

- **Domain Object (DO)**: An object that carries domain data and domain behavior.
- **Repository**: Centralize the loading and saving of aggregate roots while hiding databases, caches, and other infrastructure.
- **Anti-corruption Layer / Facade**: Translate external-context models, requests, and responses into the local model.
- **Application Service**: Orchestrate use cases, domain services, and context integration to expose application capabilities.
- **DTO / DO / PO**: Represent external interaction, the domain model, and the persistence model respectively, with explicit responsibility-based conversions.
- **Context Integration**: Connect bounded contexts through open services, HTTP/RPC, or publish-subscribe messaging.
- **Separated Domain**: Isolate a clearly bounded domain as a module, service, or independently deployable unit.
