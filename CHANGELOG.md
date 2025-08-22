# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Added
- Some missing error schemas
  - 400
  - 403

### Changed
- Reverted back to 3.0.3 due to tooling compatibility
- Updated description, moved to a separate Markdown file
- Updated various params and filenames for clarity

### Removed
- Collapsed the `RecordsZoneName` parameter into `ZoneName`
  - This was redundant and an artifact of how our Postman collection is structured

## [0.1.1] - 2025-08-19

### Changed
- Upgraded OpenAPI specification from 3.0.3 to 3.1.1
- Restructured path files for better organization and OpenAPI 3.1 compliance
- Fixed Spectral validation configuration to handle OpenAPI 3.1 schema validation
- Updated GitHub Actions workflow to use `npx` prefix for Redocly commands

### Fixed
- Resolved validation errors caused by incorrect path item structures
- Fixed false positive schema validation issues in Spectral for OpenAPI 3.1
- Corrected file naming: `platform.yaml` → `version.yaml` for clarity

## [0.1.0] - 2025-08-18

### Added
- OpenAPI 3.0.3 spec organized by resource: Authorization, Platform, Zones, Records, Tasks
- Modular structure with shared components (Zone, RRSet, WebForward, TokenResponse), pagination envelopes, common params, and standardized errors
- Automated validation via Spectral and GitHub Actions
- Documentation: Swagger UI in `docs/` using bundled spec `docs/openapi.yaml` (bundled with Redocly CLI on release)
- Project docs: README and CONTRIBUTING
