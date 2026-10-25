# Modular Monolith

Use for substantial business responsibilities with explicit public boundaries and one deployment unit.

```text
project/
  <project-manifest>
  src/
    modules/
      orders/
        public.<ext>
        domain/
          order.<ext>
          pricing.<ext>
        application/
          place-order.<ext>
          ports.<ext>
        infrastructure/
          order-store.<ext>
        transport/
          order-handler.<ext>
      notifications/
        public.<ext>
        sender.<ext>      # Simple modules remain simple
    bootstrap.<ext>
  tests/
    contracts/
    integration/
```

Domain owns rules; application orchestrates use cases; infrastructure implements required capabilities; transport maps external input. Outer implementations depend on inner contracts. Consumer-owned ports are useful when provider details otherwise leak.

Assign schema, migration, and write ownership even with one database. Enforce public access and dependency direction using ecosystem tooling. Resolve cycles through ownership or orchestration; merge a mistaken split rather than hiding it in a universal shared model.

Extract packages when dependency declarations, reuse, exports, or builds need stronger boundaries. Extract services only for operational needs.
