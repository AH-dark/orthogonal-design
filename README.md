# Orthogonal Design

A compact agent skill for designing software around independent reasons for change, derived from [AHdark’s article](https://www.ahdark.blog/decoupling-and-orthogonal-design-in-architectural-evolution/).

## Install

```sh
bunx skills add AH-dark/orthogonal-design --skill orthogonal-design
```

For Codex only, add `--agent codex`. Add `--global` for user-wide installation; the default is project-local.

## Use

Ask your agent to use `orthogonal-design` to review coupling, plan a refactor, or define module boundaries. For example:

> Use orthogonal-design to isolate pricing changes from payment providers in this checkout flow. Keep the implementation as small as the current requirements allow.

The [skill](skills/orthogonal-design/SKILL.md) contains the decision process. The [layout reference](skills/orthogonal-design/references/layouts.md) provides concrete feature, layered-module, and workspace structures without requiring any one of them.

Uses the standard `skills/<name>/SKILL.md` layout with `name` and `description` frontmatter. No runtime dependencies or npm publishing are required. See the [skills CLI documentation](https://github.com/vercel-labs/skills/blob/main/docs/creating-skills.md).
