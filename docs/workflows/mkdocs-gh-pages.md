# MkDocs GitHub Pages Publisher

This reusable workflow automates the process of building and deploying MkDocs documentation to GitHub Pages, while also incorporating key repository files (README, CHANGELOG, LICENSE) into the documentation structure.

## Overview

The workflow handles:

- Setting up Python environment
- Installing dependencies
- Creating documentation directory structure
- Copying repository files to documentation
- Creating a repository index page
- Updating MkDocs configuration
- Deploying to GitHub Pages

## Usage

### Basic Implementation

```yaml
name: Deploy MkDocs

on:
  push:
    branches:
      - main

jobs:
  deploy_docs:
    uses: suny-upstate-cwt/github.toolkit/.github/workflows/mkdocs-gh-pages.yml@main
```

### Advanced Implementation

```yaml
name: Deploy MkDocs

on:
  push:
    branches:
      - main

jobs:
  deploy_docs:
    uses: suny-upstate-cwt/github.toolkit/.github/workflows/mkdocs-gh-pages.yml@main
    with:
      python-version: '3.9'
      requirements-file: 'docs/requirements.txt'
      readme-source: 'custom/README.md'
      readme-destination: 'docs/custom/README.md'
```

## Configuration Options

| Input | Description | Default | Required |
|-------|-------------|---------|----------|
| `python-version` | Python version to use | `'3.x'` | No |
| `requirements-file` | Path to requirements.txt | `'requirements.txt'` | No |
| `readme-source` | Source path for README.md | `'README.md'` | No |
| `readme-destination` | Destination path for README.md | `'docs/repo/inc/README.md'` | No |
| `changelog-source` | Source path for CHANGELOG.md | `'CHANGELOG.md'` | No |
| `changelog-destination` | Destination path for CHANGELOG.md | `'docs/repo/inc/CHANGELOG.md'` | No |
| `license-source` | Source path for LICENSE.md | `'LICENSE.md'` | No |
| `license-destination` | Destination path for LICENSE.md | `'docs/repo/inc/LICENSE.md'` | No |

## Prerequisites

1. Repository must have MkDocs configured
2. `requirements.txt` file must include required packages:
   - `mkdocs`
   - `ruamel.yaml`
   - Any additional theme or plugin packages
3. GitHub Pages must be enabled for the repository
4. Appropriate GitHub Actions permissions must be configured

## File Structure

The workflow creates and expects the following structure:

```text
docs/
├── repo/
│   ├── inc/
│   │   ├── README.md
│   │   ├── CHANGELOG.md
│   │   └── LICENSE.md
│   └── index.md
```

## Generated Repository Index

The workflow generates a tabbed repository index page (`docs/repo/index.md`) that includes:

- README.md content
- CHANGELOG.md content
- LICENSE.md content

## MkDocs Configuration Updates

The workflow automatically updates your `mkdocs.yml` configuration to:

1. Add repository documentation to navigation
2. Maintain existing configuration
3. Add necessary settings for repository file inclusion

## Error Handling

The workflow handles missing files gracefully:

- Continues execution if optional files are missing
- Creates necessary directories automatically
- Provides clear error messages in the workflow logs

## Security Considerations

The workflow:

- Uses secure Python package installation
- Operates with minimal required permissions
- Handles files securely
- Avoids exposing sensitive information

## Troubleshooting

Common issues and solutions:

1. **Missing Requirements**
    - Ensure all required packages are in `requirements.txt`
    - Check Python version compatibility

2. **Navigation Issues**
    - Verify `mkdocs.yml` file exists
    - Check file paths are correct

3. **Deployment Failures**
    - Confirm GitHub Pages is enabled
    - Verify branch permissions

## Support

For issues with this workflow:

1. Check the workflow run logs
2. Review this documentation
3. Create an issue with:
    - Workflow version used
    - Configuration details
    - Error messages
    - Repository context (if public)
