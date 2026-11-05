# platform-workflows

Reusable GitHub Actions workflows for the Golden Path.

## Workflows

- `.github/workflows/deploy-azure-container-apps.yml`: authenticates to Azure using Service Principal + Client Secret, initializes Terraform with an Azure Storage backend, applies infrastructure, builds the caller repository's `app/` folder with ACR Tasks, and applies the resulting image.
- `.github/workflows/destroy-azure-container-apps.yml`: manually destroys the Terraform-managed application infrastructure after matching the project name.

## Calling these workflows

The application repository should call the workflow with `workflow_call`, passing the project name, Service Principal Object ID, Azure region, state storage details, and Azure secrets. See `aldo2510/golden-path-template`.

## Azure prerequisites

1. Create an Azure Storage account and blob container once for Terraform state.
2. Give the deployment Service Principal **Storage Blob Data Contributor** on the state container/storage account.
3. The Service Principal also needs permission to create the required Azure resources and role assignments (for this workshop, an administrator can assign suitable permissions in advance).
4. Add the four Azure credential secrets in the application repository.

OIDC is intentionally not used in this workshop; credentials are passed as GitHub Actions secrets. Do not commit secrets or state files.
