# Introduction
To be able to use App Configuration in ASP.NET Core, the first step is to create and setup the App Configuration store itself.
# Steps
1. Create a new App Configuration store in Azure Portal.
	- Select role based access control instead of the classic access policy.
2. Assign your user the proper RBAC-roles in order to modify the contents.
	- The creator of the resource will have the **Owner**-role, but that gives only control plane permissions.
	- Data Plane permissions can be granted with the role **App Configuration Data Owner** More on the subject here [[Authorize App Configuration Access with Entra ID]]
3. Use the data plane permissions to add configuration or feature flags
4. Continue to [[Connect to App Configuration in ASP.NET Core]]
# Sources
https://learn.microsoft.com/en-us/azure/azure-app-configuration/quickstart-azure-app-configuration-create?tabs=azure-portal#create-an-app-configuration-store

