# Repository Guidelines

## Project Structure & Module Organization
The OpenAPI root spec lives in `spec/openapi.yaml` and should only contain top-level metadata and `$ref` pointers. Place operation definitions under `spec/paths/` with hyphenated filenames that describe the resource and action, such as `zones-zoneMeta-rrsets.yaml`. Shared schemas, parameters, and responses belong in `spec/components/`, mirroring the directory structure already in use. Generated assets reside in `docs/`; `docs/openapi.yaml` is overwritten by bundling and `docs/index.html` powers the published Redoc viewer. Tooling configuration is tracked in `package.json`, `redocly.yaml`, and `.spectral.yaml`.

## Build, Test, and Development Commands
- `npm install` installs the Redocly CLI (requires Node 16+).
- `npm run lint` executes `redocly lint spec/openapi.yaml` with the repo rules.
- `npm run bundle` merges the modular spec into `docs/openapi.yaml`; commit the result when it changes.
- `npm run preview` starts a local Redoc preview (requires `redocly login` once).
- `npx spectral lint spec/openapi.yaml --ruleset .spectral.yaml` checks the custom Spectral policy used in CI.

## Coding Style & Naming Conventions
Use two-space indentation in YAML and keep keys grouped logically (metadata, request bodies, responses). Name operations and components in `kebab-case`, matching existing patterns (`tasks-taskMeta-result`). Prefer `$ref` for reusable content; inline only when a value is truly unique. Always include concise `summary`, `description`, and realistic example payloads that reflect current UltraDNS behavior.

## Testing Guidelines
Run `npm run lint` and the Spectral command before every commit; both must pass with no warnings. After `npm run bundle`, diff `docs/openapi.yaml` to confirm `$ref` targets resolved as expected. Ensure every new path defines `operationId`, success and error responses, and links to shared schemas where possible. When adding examples, validate them against schemas locally to avoid CI failures.

## Commit & Pull Request Guidelines
Follow the conventional commit style used in history (`feat`, `fix`, `chore`, `docs`) and keep subject lines under 72 characters. Synchronize spec updates and bundled output within the same commit to keep reviewers oriented. Branch names should be descriptive (`feature/zones-snapshot`, `fix/tasks-timeout`). Pull requests must include a concise change summary, note any breaking or version-specific impact, link to tracking issues, and attach screenshots or preview URLs when documentation rendering changes.
