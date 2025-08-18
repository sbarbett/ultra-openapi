# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [0.1.0] - 2025-08-28

### Added
- OpenAPI 3.0.3 spec organized by resource: Authorization, Platform, Zones, Records, Tasks
- Modular structure with shared components (Zone, RRSet, WebForward, TokenResponse), pagination envelopes, common params, and standardized errors
- Automated validation via Spectral and GitHub Actions
- Documentation: Swagger UI in `docs/` using bundled spec `docs/openapi.yaml` (bundled with Redocly CLI on release)
- Project docs: README and CONTRIBUTING
