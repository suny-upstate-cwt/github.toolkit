# GitHub Actions Workflows

This section contains documentation for all available reusable workflows in the SUNY Upstate CWT GitHub Toolkit. Each workflow is designed to be easily integrated into your repositories and customized for your specific needs.

## Available Workflows

### Documentation Workflows

- [Build and Deploy MkDocs to gh-pages Branch](flows.mkdocs-gh-pages.md) - Automates the process of building and deploying MkDocs documentation to GitHub Pages, including repository file integration.

## Workflow Categories

Our workflows are organized into the following categories:

### Documentation Generation

- MkDocs deployment
- API documentation
- Code documentation

### *Future Categories*

The following categories are planned for future development:

- Release Management
- Code Quality
- Deployment Automation
- Security Scanning
- Testing Automation

## Using Our Workflows

To use any of our reusable workflows in your repository:

1. Add a new workflow file in your repository's `.github/workflows/` directory
2. Reference the desired workflow using the `uses` keyword:

    ```yaml
    name: Your Workflow Name

    on:
    push:
        branches:
        - main

    jobs:
    documentation:
        uses: suny-upstate-cwt/github.toolkit/.github/workflows/workflow-name.yml@main
        with:
        # Configure any required inputs here
    ```

3. Configure any necessary inputs or secrets as specified in the workflow's documentation

## Best Practices

When using our reusable workflows:

- Always specify a version tag or SHA for workflow references
- Review the workflow documentation for required inputs and secrets
- Test workflows in a development environment before deploying to production
- Monitor workflow runs and set up appropriate notifications

## Workflow Development Status

- ✅ Active: Workflows that are fully tested and ready for production use
- 🔄 Beta: Workflows that are being tested but may need refinement
- 📋 Planned: Workflows that are in the planning or development stage

| Workflow | Status | Latest Version |
|----------|---------|----------------|
| MkDocs GitHub Pages | ✅ Active | v1 |
| Prepare Release | 📋 Planned | v1 |
