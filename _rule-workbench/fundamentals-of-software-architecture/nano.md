# OBEY Fundamentals of Software Architecture by Mark Richards and Neal Ford

## When to use

Use as a compact always-on architecture reminder.

## Primary bias to correct

Do not choose architecture by fashion; make trade-offs explicit and measurable.

## Decision rules

- Start with business drivers and measurable architecture characteristics.
- Prefer high cohesion, low coupling, explicit ownership, and boundaries based on behavior and change.
- Distribute only when independent deployment, scaling, fault isolation, or organizational autonomy justifies network and operational cost.
- Introduce layers, microservices, events, or brokers only for a demonstrated need.
- Record significant architecture decisions, alternatives, trade-offs, and consequences.

## Trigger rules

- Before distributing: define latency, failure, security, consistency, timeout, retry, and idempotency behavior.
- Before using events: define delivery, duplication, ordering, replay, error handling, and data-loss semantics.
- When reviewing: check the architecture against code, deployment, operations, and current business drivers.

## Final checklist

- Measurable drivers?
- Explicit trade-offs?
- Clear ownership and boundaries?
- Justified complexity?
- Governable architecture?
