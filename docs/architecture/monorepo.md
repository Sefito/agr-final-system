# Mixed-language monorepo design

Status: recommended architecture; workspace/task tooling is not configured yet.

## Why packages here

AGR has two Python execution hosts that must share document, CRM, approval and charging behavior. It also has a TypeScript frontend consuming changing HTTP/event contracts. Keeping every backend use case inside the API makes reuse depend on importing an application; copying it into a worker produces divergent rules.

Use packages for stable business responsibility and dependency ownership. Keep applications thin. Seven Python packages and two TypeScript packages are the proposed starting boundaries, not nine services or independently published products. Assistant/retrieval stay together inside intelligence. Adapters are initially grouped; split a heavy/incompatible family only when measured.

## Tool responsibilities

| Tool | Responsibility | Does not provide |
|---|---|---|
| uv workspace | Python member dependency resolution, package installation and one root Python lockfile | Import access control or business architecture |
| pnpm workspace | Web/UI/client member dependencies and one root JavaScript lockfile | Python dependency resolution |
| Nx | Cross-language task dependencies, affected work and reproducible local caching | Python environment management or automatic inference of every custom edge |
| Import Linter | Forbidden/allowed Python dependency directions and internal import contracts | Distribution dependency completeness by itself |
| TypeScript import checks/public exports | Public client/UI boundaries and forbidden app imports | Backend authorization |

Each Python member will have its own `pyproject.toml`; root workspace membership is explicit. Each JS member will have its own `package.json` and public exports. Root task/configuration files and exact pins are introduced only when implementation begins. The repository remains documentation-only.

Python members: apps/api, apps/worker, packages/access, documents, intelligence, commercial, crm, usage and adapters. JavaScript members: apps/web, packages/api-client and packages/ui. Nx can schedule all of them; it delegates language-native operations to uv/pnpm.

## Task graph and correctness

Initial target vocabulary: format/lint, typecheck, test, build, contract-generate, contract-verify and architecture-check. Add only targets with real executable behavior.

Explicit edges include business package dependencies; API contracts depend on API/public types; client generation depends on HTTP/event artifacts; web checks/build depend on api-client/UI; coordinated database tests depend on migrations and their package participants. Python edges must be declared or reliably inferred by a validated integration; do not claim Nx sees them automatically.

Cache only deterministic data-free operations with complete inputs/outputs. Include relevant manifests/locks, tool versions, transitive package sources, contracts and configuration. Migration/schema changes invalidate database checks. Root dependency changes trigger conservative verification where precise analysis is uncertain. Deployment, source sync, mutation and live-provider validation are not cached successes.

Remote caching is not selected. Terminal output and task artifacts can contain sensitive material even if source hashes are safe. No customer logs/documents/tokens enter a shared cache.

## Release and isolation

Start with one coordinated release/configuration digest. Python distributions can be built as wheels without public registry publication; production installs the selected host's dependency closure, not editable links to developer source paths. API/worker image sharing is optional and does not require every model/extraction extra.

A shared uv environment can hide undeclared dependencies. Verify package installation/tests in an isolated environment with only declared dependencies, and separately check imports. The workspace lock's consistent resolution is not proof of architecture isolation.

Do not add Bazel, an internal package registry, independently versioned domain releases or a generic event bus merely to organize the repository. Nx is recommended for this mixed task graph; it remains replaceable if measured maintenance cost outweighs the benefit.

Sources: [uv workspaces](https://docs.astral.sh/uv/concepts/projects/workspaces/), [pnpm workspaces](https://pnpm.io/workspaces), [Nx task caching](https://nx.dev/docs/concepts/how-caching-works), [Import Linter forbidden contracts](https://import-linter.readthedocs.io/en/stable/contract_types/forbidden/).
