# OBEY Fundamentals of Software Architecture by Mark Richards and Neal Ford

## When to use

Use for architecture design, review, evolution, and technology or architecture-style selection.

## Primary bias to correct

Architecture is a set of explicit trade-offs and measurable constraints, not a fashionable diagram or framework choice.

## Decision rules

- Start from business drivers and measurable architecture characteristics; choose the least-worst fit.
- Distinguish architecture decisions from design principles and record significant decisions with alternatives and consequences.
- Keep high cohesion, low coupling, and weak, local connascence; place behavior and data with the concepts that change together.
- Identify components from workflows, responsibilities, ownership, and change patterns—not database entities alone.
- Choose monolithic or distributed deployment from consistency, independent deployment, scaling, fault isolation, and organizational needs.
- Treat latency, failure, security, serialization, consistency, and operational cost as first-class distributed-system concerns.
- Use synchronous communication by default; use asynchronous communication only when its decoupling or resilience benefits justify added complexity.
- Introduce microservices, brokers, layers, or other mechanisms only when explicit architecture characteristics require them.
- Make important architecture characteristics measurable and govern them with fitness functions or repeatable checks.
- Design for credible change scenarios, but reject speculative flexibility and unnecessary indirection.

## Trigger rules

- When choosing a style, compare its characteristic strengths, weaknesses, trade-offs, and operational burden against the actual drivers.
- When splitting components or services, check transaction boundaries, data ownership, workflow coupling, and ripple effects.
- When distributing a system, define timeout, retry, idempotency, delivery, ordering, replay, recovery, and observability semantics.
- When using events, define duplication, error handling, and data-loss prevention before implementation.
- When reviewing architecture, verify diagrams and decisions against code, deployment, and operational reality.
- When inherited assumptions or architecture axioms no longer fit current conditions, challenge and replace them explicitly.

## Final checklist

- Business drivers and measurable characteristics?
- Explicit trade-offs and decision records?
- Boundaries based on behavior and ownership?
- Distribution justified and failure semantics defined?
- Governance and evolution mechanism?
