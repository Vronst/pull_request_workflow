# pull_request_workflow

This repository contains reusable GitHub Actions workflows for consistent automation across multiple projects.

## 🔁 Reusable Pull Request Workflow

### Usage

```yaml
# Exapmle job
name: test

on:
  push:
    branches:
      - stage

# needed permissions
permissions:
  contents: write
  packages: write

# This is most important part
# This uses release workflow
jobs:
  release:
    uses: Vronst/pull_request_workflow/.github/workflows/pull_request.yml@1.0.0
    with:
      head: 'head_branch'
      base: 'base_branch'
      title: 'Thats PR title'
      body: 'And thats PR body'
      flag: '--draft'  # multiple others can be used in one string
    secrets:
      TOKEN: ${{ secrets.PRO_TOKEN }}
```

- PRO_TOKEN = token with permission to create releases
