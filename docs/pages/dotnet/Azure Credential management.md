# DefaultAzureCredential in .NET

## Overview

The [DefaultAzureCredentials](https://learn.microsoft.com/en-us/dotnet/api/azure.identity.defaultazurecredential?view=azure-dotnet) class provides a default [TokenCredential](https://learn.microsoft.com/en-us/dotnet/api/azure.core.tokencredential?view=azure-dotnet) authentication flow for applications deployed in Azure. This enables the developer to
skip the explicit configuration of credentials in the code, and instead rely on the Azure SDK to authenticate using the most appropriate credential type available.

The following credential types, if enabled, will be tried, in order:

1. [EnvironmentCredential](https://learn.microsoft.com/en-us/dotnet/api/azure.identity.environmentcredential?view=azure-dotnet)
2. [WorkloadIdentityCredential](https://learn.microsoft.com/en-us/dotnet/api/azure.identity.workloadidentitycredential?view=azure-dotnet)
3. [ManagedIdentityCredential](https://learn.microsoft.com/en-us/dotnet/api/azure.identity.managedidentitycredential?view=azure-dotnet)
4. [SharedTokenCacheCredential](https://learn.microsoft.com/en-us/dotnet/api/azure.identity.sharedtokencachecredential?view=azure-dotnet)
5. [VisualStudioCredential](https://learn.microsoft.com/en-us/dotnet/api/azure.identity.visualstudiocredential?view=azure-dotnet)
6. [VisualStudioCodeCredential](https://learn.microsoft.com/en-us/dotnet/api/azure.identity.visualstudiocodecredential?view=azure-dotnet)
7. [AzureCliCredential](https://learn.microsoft.com/en-us/dotnet/api/azure.identity.azureclicredential?view=azure-dotnet)
8. [AzurePowerShellCredential](https://learn.microsoft.com/en-us/dotnet/api/azure.identity.azurepowershellcredential?view=azure-dotnet)
9. [AzureDeveloperCliCredential](https://learn.microsoft.com/en-us/dotnet/api/azure.identity.azuredeveloperclicredential?view=azure-dotnet)
10. [InteractiveBrowserCredential](https://learn.microsoft.com/en-us/dotnet/api/azure.identity.interactivebrowsercredential?view=azure-dotnet)

### Setup in a .NET console application

1. Add the `Azure.Identity` nuget package to your project. This includes the Azure SDK client library for Azure Identity.

```sh
> dotnet add package Azure.Identity
```

2. Create a new instance of the `DefaultAzureCredential` class.

```csharp
using Azure.Identity;
var credential = new DefaultAzureCredential();
```

3. Use, for example, to fetch a key from Azure Key Vault.

```csharp
using Azure.Security.KeyVault.Secrets;
var client = new KeyClient(new Uri("https://<key-vault-name>.vault.azure.net/"), credential);
var key = await client.GetKeyAsync("<key-name>");
```
