---
name: orthogonal-design
description: Design or refactor software boundaries around independent reasons for change. Use when reviewing coupling, defining module contracts, or evolving directories into packages.
---

# Orthogonal Design

Keep each change within the boundary that owns its meaning. Optimize for how much unrelated knowledge a change requires, not the number of files, interfaces, or layers.

## Method

1. Start with a concrete expected change. Trace its rules, dependencies, data, and side effects; distinguish necessary business relationships from accidental implementation dependencies.
2. Group decisions that change for the same business reason. Hide volatile decisions behind the smallest useful public contract. Similar fields or historical co-changes alone do not establish shared ownership.
3. Define contracts by observable behavior: inputs, outcomes, invariants, failure, and timing. Type compatibility does not establish substitutability. Evolve the contract when a new capability changes its meaning.
4. Make dependencies follow ownership. Let consumers define required capabilities when provider details would otherwise leak; translate genuine differences at integration boundaries and select implementations near the entry point. A stable, semantically suitable public API may be used directly.
5. Examine coupling beyond imports: shared schemas and writes, sequencing, latency, retries, and partial failure. Asynchronous delivery moves these obligations; it does not remove them.
6. Choose the smallest structural change that isolates the decision. Preserve behavior before moving files, then constrain public access and dependency direction. Use the [layout reference](references/layouts.md) only when choosing a concrete structure.
7. Rehearse the original change. Identify what must change, what should remain independent, and why. Verify behavior, contract compatibility, and declared dependency rules separately; include a deliberately illegal dependency when adding a boundary check.

## Guardrails

- Independent implementation changes may still change downstream business results. Do not erase genuine relationships to make a dependency graph look cleaner.
- Avoid speculative interfaces, universal shared models, forwarding-only adapters, and uniform layers. Resolve cycles by examining ownership or orchestration; merging a mistaken split can be correct.
- Treat type imports, re-exports, aliases, and shared data as dependencies. Package exports restrict supported entry points, not filesystem access or security.
- Introduce packages for real dependency, reuse, or build needs; introduce services for real deployment or operational needs. Neither follows automatically from a folder boundary.

## Result

Explain the change driver, ownership and contract decisions, expected propagation, and verification. For implementation tasks, apply the smallest justified change; for reviews, cite concrete evidence and prioritize actionable findings. State remaining uncertainty without claiming that a clean import graph proves independence.

Derived from AHdark's [Decoupling and Orthogonal Design in Architectural Evolution](https://www.ahdark.blog/decoupling-and-orthogonal-design-in-architectural-evolution/).
