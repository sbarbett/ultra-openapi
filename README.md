# UltraDNS OpenAPI Specification

This repository contains the OpenAPI 3.0.3 specification for the UltraDNS REST API.

## Documentation

Interactive API documentation is available in the [`docs/`](docs/) folder:

- **Swagger UI**: Open `docs/index.html` in your browser for interactive API exploration
- **Bundled Spec**: The complete OpenAPI specification is bundled as `docs/openapi.yaml`

The documentation is automatically updated on each GitHub release using Redocly.

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for detailed guidelines on how to contribute to this specification.

## Validation

The specification is automatically validated by Spectral on pull requests and pushes to main via GitHub Actions. For local validation:

```bash
spectral lint spec/openapi.yaml --ruleset .spectral.yaml
```