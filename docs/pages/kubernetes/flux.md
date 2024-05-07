---
title: Flux
layout: default
---

# Bearer Token authentication with Flux

[Flux](https://fluxcd.io/) supports [Bearer Token](https://www.oauth.com/oauth2-servers/access-tokens/) authentication while bootstrapping the service. This is a fairly undocumented process that is mentioned in
the [flux bootstrap git](https://fluxcd.io/flux/cmd/flux_bootstrap_git/) options list. 

## Why use Bearer Token authentication?

The default recommended way to bootstrap and reconcile the cluster configuration repository is to use Azure DevOps Personal Access Tokens (PAT), but they have the weaknesses:
1. The PAT is tied to a user account:
    - If the user leaves the organization, or the user's permissions change, the PAT will be invalidated.
2. The PAT has a limited lifespan, and it needs to be regenerated periodically.   
3. The PAT has a long lifespan, so if it is compromised, it can be used to access the organization's resources for a long time.

To overcome these weaknesses, an OAuth2 bearer token can be used to access Azure Repos. The bearer token is tied to a managed identity, and it has a [random lifespan between 60 to 90 minutes](https://learn.microsoft.com/en-us/entra/identity-platform/access-tokens#token-lifetime). This forces the service to refresh the token periodically, and limits the time window for an attacker to use the token.

## Workflow

These steps need to be taken to use Bearer Token authentication with Flux:
1. Create a user assigned managed identity in Azure.
2. Assign the managed identity the necessary permissions to access the Azure Repos.
    - The identity needs read-level access to the project
    - The identity needs read & write -level access to the repository. This can be achieved with the `Contributor` role.
3. Bootstrap flux with either a repository constrained personal access token, or a bearer token for the developer identity.
    - The bearer token is less secure in this case, as it will give complete control to the repository and everything the user has access to in Azure DevOps.
4. Write a kubernetes deployment that logs in to Azure, and then fetches the Azure DevOps access token.
5. Assign the managed identity to the kubernetes deployment.

