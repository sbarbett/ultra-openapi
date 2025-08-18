# UltraDNS API Documentation

This directory contains the automatically generated API documentation for the UltraDNS OpenAPI specification.

## Files

- `index.html` - Swagger UI interface for interactive API documentation
- `openapi.yaml` - Bundled OpenAPI specification (auto-generated on releases)

## How it works

1. The OpenAPI specification is defined in the `spec/` directory with modular YAML files
2. On each GitHub release, Redocly automatically bundles all the spec files into a single `openapi.yaml`
3. The bundled spec is served by the Swagger UI interface

## Local Development

To preview the documentation locally:

```bash
# Install dependencies
npm install

# Bundle the spec locally
npm run bundle

# Preview with Redocly
npm run preview
```