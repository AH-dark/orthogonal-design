# Single-Purpose Program

Use for one cohesive command, script, library, or small application.

```text
project/
  <project-manifest>
  src/
    main.<ext>           # Entry point, when executable
    logic.<ext>          # Extract only when a separate rule warrants it
  tests/
    logic.test.<ext>
```

A single source file may suffice. Follow native conventions for a library entry point, notebook, or script. Add interfaces only when a real boundary needs them.

Move toward feature organization when distinct use cases acquire independent reasons to change. File length alone is not the trigger.
