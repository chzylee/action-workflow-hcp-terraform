# action-workflow-hcp-terraform-run

Reusable Workflow for GitHub Actions to start HCP Terraform runs for a workspace.

## Usage

**This workflow assumes the given HCP Workspace exists already.**

This repository provides a reusable GitHub Actions workflow for running Terraform operations using HCP Terraform. Follow the example below to see how to use this action in a GitHub Action.

### Example

In your repository, create a workflow file (e.g., `.github/workflows/deploy.yml`) with the following content:

```yaml
name: Deploy Infrastructure

on:
  workflow_dispatch:

jobs:
  deploy:
    uses: chzylee/action-workflow-hcp-terraform-run@v1.1.1
    with:
      terraform_directory: ./terraform # Action run from context of the repository root
      tfc_organization: ${{ env.HCP_TERRAFORM_ORG }}
      tfc_workspace: ${{ env.HCP_TERRAFORM_WORKSPACE }}
      tfc_token: ${{ secrets.TF_API_TOKEN }}
```

### Inputs

| Name                | Description                       | Required | Example            |
| ------------------- | --------------------------------- | -------- | ------------------ |
| tfc_hostname        | Terraform Cloud hostname          | Yes      | `app.terraform.io` |
| tfc_organization    | Terraform Cloud organization name | Yes      | `my-org`           |
| tfc_workspace       | Terraform Cloud workspace name    | Yes      | `my-space`         |
| terraform_directory | Path to Terraform code directory  | Yes      | `./terraform`      |
| tfc_token           | HCP Terraformm API Token          | Yes      | `secret`           |

---
