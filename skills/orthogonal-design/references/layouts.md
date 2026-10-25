# Layout Reference

Choose a layout from actual change pressures. Names are illustrative; retain the project's language and conventions.

## Small application: feature ownership

```text
src/
  orders/
    order.ts
    pricing.ts
    place-order.ts
    index.ts                 # Deliberate public surface
  payments/
    api.ts
    provider.ts
    index.ts
  app.ts                     # Select and connect implementations
```

Keep simple rules as functions. A directory groups code; it does not enforce access restrictions.

## Complex feature: internal separation

```text
src/modules/orders/
  index.ts
  domain/
    order.ts                 # Business invariants
    pricing.ts
  application/
    place-order.ts           # Use-case orchestration
    ports.ts                 # Capabilities required by this use case
  infrastructure/
    postgres-orders.ts       # Implements persistence capability
  transport/
    order-http.ts            # Maps requests and responses
src/bootstrap.ts             # Composition root
```

Infrastructure and transport depend on inner contracts. Domain rules do not import application or infrastructure details. Runtime calls through injected ports may flow in the opposite direction to source dependencies. Create only layers with a distinct responsibility.

## Workspace: explicit package boundaries

```text
apps/shop/src/
  main.ts                    # Composition root
  integrations.ts            # Maps public contracts when semantics differ
packages/
  checkout/
    package.json
    src/
      index.ts
      domain/pricing.ts
      application/checkout.ts
      application/ports.ts   # Consumer-owned contracts
  payments/
    package.json
    src/
      index.ts
      api.ts                 # Provider's public contract
      internal/provider.ts
  notifications/
    package.json
    src/
      index.ts
      api.ts
      internal/sender.ts
tests/
  contracts/
  integrations/
```

In this arrangement, integration code depends on each package's public API; checkout does not import provider internals. Export only intended entries and enforce dependency rules against deep imports, cross-package relative paths, aliases, and cycles using the project's existing tooling. Keep data ownership explicit even in one database. These packages may still deploy together.

## Check the boundary against a change

| Change | Expected impact |
| --- | --- |
| Discount policy | Pricing and its tests; payment receives a different amount unchanged. |
| Compatible payment provider | Adapter, wiring, and contract tests. |
| Immediate payment becomes pending | Result contract, state transitions, and notification timing must evolve. |
| Discount depends on payment method | Pass the necessary eligibility facts; keep pricing ownership explicit. |

For asynchronous notifications, specify durable handoff, retries, and duplicate effects. A local outbox transaction does not include a third-party charge; deleting an `await` does not establish reliable delivery.
