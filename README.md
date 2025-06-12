# action-workflow-hcp-terraform

Reusable Workflow for GitHub Actions to run Terraform via HCP Terraform

## Usage

This repository provides a reusable GitHub Actions workflow for running Terraform operations using HCP Terraform. You can call this workflow from another repository using the `workflow_call` event.

### Example

In your repository, create a workflow file (e.g., `.github/workflows/deploy.yml`) with the following content:

```yaml
name: Deploy Infrastructure

on:
  workflow_dispatch:

jobs:
  deploy:
    uses: chzylee/action-workflow-hcp-terraform/.github/workflows/action_terraform.yml@v1.0.0
    with:
      environment: 'dev'
      tfcode_path: './terraform'
      tfc_organization: 'your-tfc-org'
      tfc_hostname: 'app.terraform.io'
      tfc_workspace: 'your-workspace'
    secrets:
      TF_API_TOKEN: ${{ secrets.TF_API_TOKEN }}
```

### Inputs

| Name             | Description                       | Required | Example            |
| ---------------- | --------------------------------- | -------- | ------------------ |
| environment      | Environment to deploy to          | Yes      | `dev`              |
| tfcode_path      | Path to Terraform code directory  | Yes      | `./terraform`      |
| tfc_organization | Terraform Cloud organization name | Yes      | `my-org`           |
| tfc_hostname     | Terraform Cloud hostname          | Yes      | `app.terraform.io` |
| tfc_workspace    | Terraform Cloud workspace name    | Yes      | `my-workspace`     |

### Secrets

| Name         | Description               | Required |
| ------------ | ------------------------- | -------- |
| TF_API_TOKEN | Terraform Cloud API token | Yes      |

---
