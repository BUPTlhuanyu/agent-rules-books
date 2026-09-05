# OBEY Fundamentals of Software Architecture by Mark Richards and Neal Ford

## Source and status

This rule set is distilled from *Fundamentals of Software Architecture: An Engineering Approach* (Mark Richards and Neal Ford, O'Reilly, 2020). It is a draft derived from the supplied PDF and requires human review before release.

## Purpose

Use this policy when designing, reviewing, or evolving software architecture. Treat architecture as the set of important structural decisions, architecture characteristics, and design principles that shape the system and its ability to change.

## Architectural thinking

- Architects MUST understand the business drivers before choosing an architecture style or technology.
- Architects MUST distinguish architecture decisions (constraints and allowed structures) from design principles (guidance for making local design choices).
- Architects SHOULD maintain technical breadth and understand the trade-offs of technologies rather than becoming an advocate for one tool or style.
- Architects MUST make trade-offs explicit. There is no universally best architecture; choose the least-worst fit for the stated priorities.
- Architects SHOULD balance architecture work with enough hands-on implementation to keep decisions grounded in reality.
- Architects MUST continually analyze the architecture and verify that it still supports current business and operational needs.
- Architects MUST question inherited axioms and assumptions when technology, business conditions, or operational constraints change.

## Architecture characteristics

- Teams MUST identify the architecture characteristics that materially affect the system, such as performance, scalability, availability, reliability, security, observability, deployability, testability, and maintainability.
- Teams MUST distinguish explicit characteristics stated in requirements from implicit characteristics revealed by domain, operational, legal, or organizational concerns.
- Teams MUST define characteristics in a measurable or testable form. Avoid vague goals such as “fast,” “secure,” or “scalable” without scenarios and thresholds.
- Teams SHOULD keep the set of critical characteristics small enough to make trade-offs visible. Every added characteristic increases constraint and cost.
- Teams MUST treat cross-cutting characteristics as architectural concerns rather than leaving them to accidental local implementation.
- Teams SHOULD govern important characteristics with fitness functions, automated checks, or other repeatable measures.
- Teams MUST revisit architecture characteristics as scope, scale, organization, and deployment context change.

## Modularity and boundaries

- Teams MUST seek high cohesion and low coupling, while recognizing that coupling has different strengths and forms.
- Teams SHOULD place behavior and data that change together together, and separate elements that change for different reasons.
- Teams MUST examine connascence: how strongly components must know or change together. Prefer static, local, and weak forms over dynamic, distributed, and strong forms.
- Teams MUST choose component boundaries from workflows, responsibilities, domain behavior, and architecture characteristics—not merely from database entities or technical layers.
- Teams SHOULD use domain partitioning when business capabilities and independent change are more important than technical similarity.
- Teams MUST reassess component granularity after assigning responsibilities and characteristics; initial partitions are hypotheses, not facts.
- Teams SHOULD make dependencies and ownership explicit and avoid boundaries that create excessive coordination or ripple effects.

## Architecture quanta and deployment

- Teams MUST determine whether the system needs a single architecture quantum or multiple independently deployable quanta.
- Teams MUST account for the cost of distributed architecture: network latency, reliability, security, serialization, operational complexity, and data consistency.
- Teams SHOULD keep functionality together when it shares strong consistency requirements and frequently crosses a boundary.
- Teams SHOULD distribute functionality only when independent deployment, scaling, fault isolation, organizational autonomy, or another explicit characteristic justifies the cost.

## Choosing architecture styles

- Teams MUST choose an architecture style from requirements and characteristics, not from fashion, familiarity, or a desire to use a particular technology.
- Layered architecture SHOULD be used when clear separation and simplicity matter, while teams watch for inappropriate layering, shared database coupling, and changes that cross every layer.
- Pipeline architecture SHOULD be used for independent sequential transformations with clear input and output contracts.
- Microkernel architecture SHOULD be used when a stable core and replaceable plug-ins are central to the product.
- Service-based architecture SHOULD be evaluated when coarse-grained services and centralized or partitioned data fit the domain; service boundaries MUST be checked for coupling and transaction problems.
- Event-driven architecture SHOULD be used when asynchronous communication, temporal decoupling, responsiveness, or independent reaction is a real requirement.
- Teams MUST NOT introduce microservices, event brokers, or distributed workflows merely to appear modern or to solve an unmeasured problem.
- Teams MUST document the strengths, weaknesses, and characteristic ratings that motivated the selected style.

## Distributed systems

- Teams MUST assume the network is not reliable, latency is not zero, bandwidth is not infinite, and transport has a cost.
- Teams MUST treat the network as insecure, changing, heterogeneous, and administered by multiple parties.
- Distributed designs MUST define timeout, retry, failure, idempotency, authentication, authorization, observability, and recovery behavior.
- Teams MUST decide deliberately where data lives and whether communication is synchronous or asynchronous.
- Use synchronous communication by default when immediate response and simple consistency are required; use asynchronous communication when temporal decoupling, resilience, throughput, or independent processing justifies the added complexity.
- Event-driven systems MUST define delivery, ordering, duplication, replay, error handling, and data-loss prevention semantics.

## Architecture decisions and risk

- Architects MUST record significant decisions, their context, considered alternatives, trade-offs, and consequences.
- Architects SHOULD record decisions at the level of architectural constraints, not every local implementation detail.
- Teams MUST analyze architecture risk before committing to an option, especially where coupling, distribution, data ownership, or operational complexity is high.
- Teams SHOULD use lightweight decision records and revisit them when assumptions or business drivers change.
- Architecture diagrams MUST communicate the intended audience, scope, boundaries, responsibilities, and runtime or deployment relationships.
- Diagrams MUST NOT be treated as architecture itself; verify them against code, deployment, and operational reality.

## Evolution and governance

- Teams MUST design for change in the characteristics that are likely to change, but MUST NOT add flexibility without a credible change scenario.
- Teams SHOULD use fitness functions and automated governance to detect architectural erosion continuously.
- Architecture governance SHOULD enable teams through guardrails and feedback rather than centralizing every design decision.
- Architects MUST account for organizational structure, team ownership, process, operations, cost, legal constraints, and political realities.
- Architects SHOULD negotiate with evidence, gather information before proposing a solution, and make cost and time explicit when other arguments fail.

## Review checklist

- Are business drivers and measurable architecture characteristics explicit?
- Are trade-offs and rejected alternatives recorded?
- Are boundaries based on behavior, ownership, workflows, and change patterns?
- Is distribution justified by a real characteristic or autonomy need?
- Are network, data, failure, security, and operational semantics explicit?
- Can the architecture be measured and governed?
- Does the design remain understandable, evolvable, and consistent with team ownership?
