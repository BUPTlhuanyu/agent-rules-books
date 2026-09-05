# OBEY Fundamentals of Software Architecture by Mark Richards and Neal Ford

Canonical full source: [full.md](full.md)

## Status

Draft. The rule set was extracted from the supplied PDF and requires human review for completeness, wording strength, and source fidelity.

## Source basis

Canonical source: `full.md`, exposed from `fundamentals-of-software-architecture/fundamentals-of-software-architecture.md`.

The PDF covers the Preface and Chapters 1–24. The extracted rule set preserves the book's recurring pressure around architecture characteristics, trade-offs, modularity, components, architecture styles, distributed systems, decisions, risk, evolution, and organizational context.

## Mini mapping

- `M1`: Start from business drivers and measurable architecture characteristics; choose the least-worst fit. Source: Chapters 1–2, 4–6.
- `M2`: Distinguish decisions from principles and record significant decisions. Source: Chapters 1–2, 19.
- `M3`: Keep cohesion high, coupling low, and connascence weak and local. Source: Chapter 3.
- `M4`: Identify components from workflows, responsibilities, ownership, and change patterns. Source: Chapter 8.
- `M5`: Choose deployment boundaries from consistency, scaling, autonomy, and operational cost. Source: Chapters 7–9, 13, 17–18.
- `M6`: Treat distributed-system failure, security, latency, serialization, and consistency as explicit concerns. Source: Chapter 9 and distributed architecture chapters.
- `M7`: Use synchronous communication by default and asynchronous communication when justified. Source: Chapters 14, 17–18.
- `M8`: Introduce architecture mechanisms only when characteristics require them. Source: Chapters 10–18.
- `M9`: Measure and govern characteristics with fitness functions. Source: Chapter 6.
- `M10`: Design for credible change and reject speculative flexibility. Source: Chapters 2, 6, 19–20.

## Nano mapping

- `N1`: Start with business drivers and measurable characteristics. Source: Chapters 1–6.
- `N2`: Prefer cohesion, low coupling, explicit ownership, and behavior-based boundaries. Source: Chapters 3 and 8.
- `N3`: Distribute only when explicit benefits justify the cost. Source: Chapters 7 and 9.
- `N4`: Introduce mechanisms only for demonstrated needs. Source: Chapters 10–18.
- `N5`: Record decisions and trade-offs. Source: Chapters 2 and 19.
- `N6`: Define distributed and event-driven failure semantics before implementation. Source: Chapters 9, 14, and 17.
- `N7`: Verify architecture against operational reality and current drivers. Source: Chapters 6, 20–22.

## Intentional compression

- Detailed descriptions and ratings of individual architecture styles were merged into style-selection rules.
- The eight distributed-computing fallacies were merged into explicit network-cost and failure-semantics rules.
- Career, negotiation, and leadership material was retained only where it changes architecture decision-making, governance, or stakeholder alignment.
- Examples and case-study narrative were intentionally omitted from `mini.md` and `nano.md`.
