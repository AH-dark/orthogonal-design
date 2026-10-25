# Orthogonal Design

A compact, English-language agent skill for scaffolding projects at any scale and evolving software boundaries. Based on [AHdark’s article](https://www.ahdark.blog/decoupling-and-orthogonal-design-in-architectural-evolution/).

## Install

```sh
bunx skills add AH-dark/orthogonal-design --skill orthogonal-design
```

Add `--agent codex` to target Codex, or `--global` for user-wide installation.

## Use

> Use orthogonal-design to scaffold this project. Choose the smallest layout that fits its business complexity, reuse, and deployment requirements; follow the selected language and framework conventions.

The [skill](skills/orthogonal-design/SKILL.md) routes to separate layouts:

- [Single-purpose program](skills/orthogonal-design/references/single-purpose.md)
- [Feature-oriented application](skills/orthogonal-design/references/feature-application.md)
- [Modular monolith](skills/orthogonal-design/references/modular-monolith.md)
- [Multi-package workspace](skills/orthogonal-design/references/package-workspace.md)
- [Independent services](skills/orthogonal-design/references/independent-services.md)

These are alternatives, not mandatory growth stages. Examples are language-neutral and adapt to native ecosystem conventions. Service-layout details extend the article's principles.

Standard `skills/<name>/SKILL.md` packaging; no runtime dependencies or npm publication required. See the [skills CLI format](https://github.com/vercel-labs/skills/blob/main/docs/creating-skills.md).
