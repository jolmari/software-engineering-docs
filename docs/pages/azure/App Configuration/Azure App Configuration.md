# Introduction
[Azure App Configuration](https://learn.microsoft.com/en-us/azure/azure-app-configuration/overview) is a service for centrally managing application settings and feature flags.

Cloud-based applications often run on multiple virtual machines or containers in multiple regions and use multiple external services. Creating a robust and scalable application in a distributed environment presents a significant challenge. An application’s configuration settings should be kept external to its executable and read in from its runtime environment or an external source.
# Benefits
App Configuration offers the following benefits:
- A fully managed service that can be set up in minutes
- Flexible key representations and mappings
- Tagging with labels
- Point-in-time replay of settings
- Dedicated UI for feature flag management
- Comparison of two sets of configurations on custom-defined dimensions
- Enhanced security through Azure-managed identities
- Encryption of sensitive information at rest and in transit
- Native integration with popular frameworks

App Configuration complements [Azure Key Vault](https://azure.microsoft.com/services/key-vault/), which is used to store application secrets.
- Centralize management and distribution of hierarchical configuration data for different environments and geographies
- Dynamically change application settings without the need to redeploy or restart an application
- Control feature availability in real-time
# Topics 
The following topics introduce App Configuration development approaches:
- [[Setting up App Configuration in Azure]]
- [[Authorize App Configuration Access with Entra ID]]
- [[Connect to App Configuration in ASP.NET Core]]
- [[Feature flagging in ASP.NET Core]]
# Sources
[What is Azure App Configuration](https://learn.microsoft.com/en-us/azure/azure-app-configuration/overview)