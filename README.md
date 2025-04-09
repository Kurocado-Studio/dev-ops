# Kurocado Studio DevOps

Please visit [the documentation](https://kurocado-studio.github.io/dev-ops)

## Repository layout (overview)

```
.github/
    ├─ actions/               # Composite actions (install, lint, deploy …)
    ├─ workflows/             # Re‑usable workflows (workflow.*.yml)
    └─ templates/             # Issue / PR templates, CODEOWNERS, etc.
Writerside/                 # Docs sources (built by workflow.document)
package.json                # Only dev‑dependencies required by actions
```

## Getting Started

1. **Clone the repository**

   ```bash
   git clone https://github.com/Kurocado-Studio/design-system.git
   cd design-system
   ```

2. **Install dependencies**

   ```bash
   pnpm install
   ```

3. **Initial setup**

   ```bash
   pnpm run setup
   ```

   The setup script installs all required packages and runs any additional initialization tasks.

## Local Development

- **Lint code**

  ```bash
  pnpm run prettier:check
  ```

## Monorepo vs single‑package

Pass `monorepo: true` when calling a workflow for Turborepo caching (commands like
`pnpm exec turbo run build/test …`). Leave it `false` for classic single‑package repositories.

## Documentation site

The latest documentation for these workflows is deployed to GitHub Pages:
<https://kurocado-studio.github.io/dev-ops/>
