# Multi-Package Workspace

Use for explicit dependency/export units, independently built components, or reuse by multiple applications. Packages may deploy together.

```text
project/
  <workspace-manifest>
  apps/
    shop/
      <app-manifest>
      src/
        main.<ext>
        integrations.<ext>
  packages/
    checkout/
      <package-manifest>
      src/
        public.<ext>
        domain/pricing.<ext>
        application/checkout.<ext>
        application/ports.<ext>
    payments/
      <package-manifest>
      src/
        public.<ext>
        api.<ext>
        internal/provider.<ext>
    notifications/
      <package-manifest>
      src/
        public.<ext>
        internal/sender.<ext>
  tests/
    contracts/
    integration/
```

Use native package manifests and workspace/build conventions. The app composes public capabilities and maps semantic differences; checkout need not import provider details. Keep each package internally as simple as its responsibility allows.

For Node, deliberate `index` exports and `package.json` exports define supported entries; `private: true` prevents publishing, not internal access. Enforce deep-import, cross-package relative-path, alias, type-import, and cycle rules as needed. Use equivalent visibility mechanisms in other ecosystems.

Share stable knowledge, not merely similar data shapes. Workspace organization makes no independent-deployment claim.
