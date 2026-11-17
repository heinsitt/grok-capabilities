# GitHub Actions Workflows in this repository

This folder contains **advanced GitHub Actions examples** that demonstrate modern best practices.

## Workflows

| File | Purpose | Key Advanced Features |
|------|---------|-----------------------|
| `ci.yml` | Main Continuous Integration | Concurrency, Path filters, Job needs, Step Summary |
| `pages.yml` | Deploy `docs/` to GitHub Pages | Environment protection, OIDC-ready permissions, Concurrency |
| `reusable-validate.yml` | Example **Reusable Workflow** | `workflow_call`, inputs, outputs |

## How to enable GitHub Pages

1. Go to **Settings → Pages**
2. Source: **GitHub Actions**
3. The `pages.yml` workflow will automatically deploy the `docs/` folder

## How to use the Reusable Workflow in another repository

In any other repository you own, create a workflow like this:

```yaml
name: Call Reusable Validate

on:
  push:
    branches: [main]
  pull_request:

jobs:
  validate:
    uses: heinsitt/grok-capabilities/.github/workflows/reusable-validate.yml@main
    with:
      run-markdown-lint: true
      run-html-check: false
```

> Note: The calling repository must have access to this repository (public repos work by default).
