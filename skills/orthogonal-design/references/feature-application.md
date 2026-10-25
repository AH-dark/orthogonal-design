# Feature-Oriented Application

Use for multiple use cases with limited internal complexity, deployed together.

```text
project/
  <project-manifest>
  src/
    orders/
      model.<ext>
      pricing.<ext>
      place-order.<ext>
      public.<ext>
    payments/
      public.<ext>
      provider.<ext>
    notifications/
      public.<ext>
      sender.<ext>
    bootstrap.<ext>       # Select and connect implementations
  tests/
    place-order.test.<ext>
```

Replace the example business names with actual capabilities. Keep related rules and use cases together; use framework-native routes or handlers where required. A simple existing technical-layer layout can remain adequate—do not move files without a change-locality benefit.

Public entries express intended access, but folders do not enforce it. Add internal layers only to features whose rules, orchestration, and external implementations change separately.
