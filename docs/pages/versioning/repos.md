---
title: Azure Repos
layout: default
---

# Azure Repos

## Perform Git operations with a Bearer Token

It is possible to perform Git operations with a Entra Id Bearer Token instead of PAT, or SSH. This is useful for scenarios where you
do not want to store a secret, and avoid the hassle of rotating the PAT.

[Q: Can I use a service principal to do git operations, like clone a repo?](https://learn.microsoft.com/en-us/azure/devops/integrate/get-started/authentication/service-principal-managed-identity?view=azure-devops#q-can-i-use-a-service-principal-to-do-git-operations-like-clone-a-repo)

## Fetching the Bearer Token for Azure DevOps (User Account)

To fetch the Bearer Token for Azure Repos, you need to follow these steps:

- Use `az login` to login to your Azure account, with the proper subscription.
- Check that you have the proper permissions to access the repository.
- Fetch the Bearer Token with the CLI command `az account get-access-token --resource <azure-devops-resource-id> --query "accessToken" --output tsv`

## Fetching the Bearer Token for Azure DevOps (Managed Identity)

[Sign in with a managed identity using Azure CLI](https://learn.microsoft.com/en-us/cli/azure/authenticate-azure-cli-managed-identity)