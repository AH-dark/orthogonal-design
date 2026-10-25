# Independent Services

Use only when capabilities require independent deployment, scaling, or operational isolation. This layout extends the article's service-extraction criteria; the article does not prescribe a service scaffold.

```text
system/
  services/
    orders/
      <service-manifest>
      src/
      tests/
      migrations/        # If this service owns persistent data
    payments/
      <service-manifest>
      src/
      tests/
  integration-tests/
  deployment/            # Only for the chosen deployment platform
```

Services may instead live in separate repositories. Choose each service's internal layout independently. Use framework-native handlers, domain contracts, and adapters; do not impose four layers everywhere.

Before splitting, establish API/event meaning, data ownership, compatibility, timeouts, partial-failure behavior, and necessary observability. Avoid direct writes into another service's data. Add messaging, orchestration, or platform files only when required by the actual workflow.

For reliable asynchronous handoff, account for durable publication and duplicate effects. A transactional outbox couples local state and message recording; it does not atomically include third-party payment. Consumers need appropriate idempotency, and external outcomes may require reconciliation.

Keep capabilities together when operational independence does not justify network and consistency costs.
