---
name: orthogonal-design
description: Scaffold projects at any scale or evolve existing structures around independent reasons for change. Use when choosing project layouts, defining module boundaries, or planning architectural refactors across languages and frameworks.
---

# Orthogonal Design

Keep change with the responsibility that owns it. Choose structure from business complexity, reuse, and operational needs—not file counts or an assumed growth path.

## Scaffold or Evolve

1. Establish the product's use cases, language/framework, runtime, and deployment constraints from the request and existing project. Ask only about consequential unknowns; state reasonable defaults.
2. Identify independently changing rules, integrations, and data owners. Separate accidental dependencies from necessary business relationships.
3. Select the smallest suitable [layout](references/layouts.md); read only the relevant reference. Different modules may use different internal structures.
4. Adapt directory names and files to the ecosystem's conventions. Create a runnable entry point, required configuration, and a minimal representative use case with appropriate verification. For an existing project, preserve behavior and change only the justified scope. Avoid empty layers, speculative abstractions, and unrelated infrastructure.
5. Define small public contracts by meaning: inputs, outcomes, invariants, errors, and timing. Keep volatile details private; translate genuine differences at integration boundaries and choose implementations near the entry point.
6. Verify the scaffold's documented run/build path and a representative behavior. Add boundary checks where boundaries need enforcement; validate new checks with an illegal dependency. Rehearse a likely change and explain its expected reach.

## Boundary Rules

- Group code by shared reasons for change, not merely similar fields or historical co-changes. Stable public APIs can be used directly; adapters and consumer-owned ports should isolate real differences.
- Keep business rules independent of external implementations. Runtime calls through injected capabilities need not follow source dependency direction.
- Include type imports, re-exports, aliases, shared data, timing, and failure in coupling analysis. An acyclic import graph alone does not prove independence.
- Preserve contract semantics across implementations. Pending work cannot masquerade as success; genuine new capabilities may require coordinated model changes.
- Establish data ownership and explicit cross-boundary access. Async work needs handoff, retry, and duplicate-effect semantics; a local transaction does not include an external side effect.
- Packages and services solve different problems. Neither more layers nor more deployment units is evidence of better design.

## Handoff

Report the chosen layout and its reason, runnable commands, verification results, and the concrete pressure that would justify a different boundary. Do not add speculative future directories.

Based on AHdark's [Decoupling and Orthogonal Design in Architectural Evolution](https://www.ahdark.blog/decoupling-and-orthogonal-design-in-architectural-evolution/). Directory examples are illustrative; service layout details extend the article's principles.
