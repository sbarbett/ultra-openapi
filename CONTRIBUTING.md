# Contributing to UltraDNS OpenAPI Specification

This project contains an OpenAPI 3.0.3 specification for the UltraDNS REST API, organized for better maintainability and reusability.

## How to Contribute

### 1. Fork the Repository
1. Go to the [ultra-openapi repository](https://github.com/ultradns/ultra-openapi)
2. Click the "Fork" button in the top-right corner
3. This creates a copy of the repository under your GitHub account

### 2. Clone Your Fork
```bash
git clone https://github.com/YOUR_USERNAME/ultra-openapi.git
cd ultra-openapi
```

### 3. Create a Branch
```bash
# Create and switch to a new branch
git checkout -b feature/your-feature-name

# Or for bug fixes
git checkout -b fix/your-bug-description
```

### 4. Make Your Changes
- Edit the appropriate files in the `spec/` directory
- Follow the development guidelines below
- Test your changes with Spectral validation

### 5. Commit Your Changes
```bash
git add .
git commit -m "prefix: Add descriptive commit message"

# Example commit messages:
# "feat: Add webforwards endpoint to zones path file"
# "fix: Fix date-time format in Zone schema examples"
# "chore: Add missing error responses for auth endpoints"
```

### 6. Push to Your Fork
```bash
git push origin feature/your-feature-name
```

### 7. Create a Pull Request
1. Go to your fork on GitHub
2. Click "Compare & pull request" for your branch
3. Fill out the PR template with:
   - Description of changes
   - Any breaking changes
   - Screenshots (if applicable)
4. Submit the PR

### 8. Review Process
- GitHub Actions will automatically run Spectral validation
- Maintainers will review your PR
- Address any feedback or requested changes
- Once approved, your PR will be merged

## Development Setup

### Prerequisites
1. **Node.js** (v14 or higher)
2. **Spectral CLI** for OpenAPI validation

### Installation
```bash
# Install Spectral CLI globally
npm install -g @stoplight/spectral-cli
```

## Validation and Linting

### Local Validation
To validate the OpenAPI specification locally:

```bash
# Validate the main specification
spectral lint spec/openapi.yaml

# Validate with custom rules
spectral lint spec/openapi.yaml --ruleset .spectral.yaml
```

### Generate Validation Report
```bash
# Generate HTML report
spectral lint spec/openapi.yaml --ruleset .spectral.yaml --format html > validation-report.html

# Generate JSON report
spectral lint spec/openapi.yaml --ruleset .spectral.yaml --format json > validation-report.json
```

## Development Workflow

### Adding New Endpoints
1. **Identify the resource domain** (auth, zones, records, etc.)
2. **Add to appropriate path file** in `spec/paths/`
3. **Reference in main file** `spec/openapi.yaml`
4. **Validate changes** with Spectral

Example:
```yaml
# In spec/openapi.yaml
paths:
  /new/endpoint:
    $ref: './paths/resource.yaml#/operation'
```

### Adding New Schemas
1. **Create schema file** in `spec/components/schemas/`
2. **Reference in path files** using `$ref: '../components/schemas/SchemaName.yaml'`
3. **Validate references** with Spectral

### Adding New Parameters
1. **Create parameter file** in `spec/components/parameters/`
2. **Reference in path files** using `$ref: '../components/parameters/ParameterName.yaml'`
3. **Ensure consistent naming** across endpoints

## Best Practices

### Schema Design
- Use proper `format` attributes (e.g., `date-time` for timestamps)
- Include `enum` values for constrained fields
- Provide meaningful `example` values
- Use `required` arrays for mandatory fields

### Parameter Consistency
- Reuse common parameters (limit, sort, reverse)
- Use consistent naming conventions
- Include proper descriptions and examples

### Error Handling
- Use standardized error response schemas
- Include appropriate HTTP status codes
- Provide meaningful error messages

### Documentation
- Keep descriptions clear and concise
- Include usage examples where helpful
- Document any UltraDNS-specific behaviors

## Validation Rules

The `.spectral.yaml` configuration includes:
- **OpenAPI 3.0 compliance** checks
- **Schema validation** for examples and media types
- **API server** configuration validation
- **Custom rules** for UltraDNS-specific patterns

## Troubleshooting

### Common Issues
1. **Invalid references**: Check that `$ref` paths are correct
2. **Schema validation errors**: Ensure examples match schema definitions
3. **Date-time format**: Use ISO 8601 format (`"2025-06-17T23:48:00Z"`)

### Getting Help
- Check Spectral documentation: https://meta.stoplight.io/docs/spectral/
- Review OpenAPI 3.0 specification: https://spec.openapis.org/oas/v3.0.3
- Validate against the UltraDNS API for accuracy
