# Choose a Layout

Select by responsibility and operational pressure, not project size alone. These are alternatives, not mandatory stages. Preserve framework-required structure and translate example filenames to the chosen language.

| Current need | Reference |
| --- | --- |
| One cohesive task, little independent variation | [Single-purpose program](single-purpose.md) |
| Several use cases in one application | [Feature-oriented application](feature-application.md) |
| Complex business modules with distinct rules and integrations | [Modular monolith](modular-monolith.md) |
| Explicit dependency/export boundaries, independent builds, or multiple consuming applications | [Multi-package workspace](package-workspace.md) |
| Independently deployed or scaled capabilities, or required operational isolation | [Independent services](independent-services.md) |

A large application can remain one deployable unit. A small system may need multiple deployment units. Workspaces can contain monoliths or services; deployment and source organization are separate choices. Use only the boundaries needed by the current task.
