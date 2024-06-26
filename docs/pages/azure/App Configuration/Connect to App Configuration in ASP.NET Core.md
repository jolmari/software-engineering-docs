%% #-🪴weedy %%
[[Unsorted]]
# Introduction
ASP.NET Core builds a single configuration object that is based on key-value pairs based on chained [configuration providers](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/configuration#configuration-providers). App Configuration has its own configuration provider, therefore it can be used as a source for your application.
## Assign Managed Identity
Add a new managed identity for ASP.NET Core host service (Functions App, App Service, ...), if not existing already. Add **App Configuration data reader** role to the managed identity. 
## Connecting to App Configuration
Connect to the App Configuration to load the stored key-value pairs into the configuration object:
1. Add configuration key-value pairs to the tarte App Configuration store.
2. Install dependency `Microsoft.Azure.AppConfiguration.AspNetCore`. 
3. Set the store endpoint to your `appsettings.json` configuration file.
4. Add the following code block to the `Program.cs` builder configuration to connect to the App Configuration store:

```csharp
builder.Configuration.AddAzureAppConfiguration(options => options.Connect( new Uri(builder.Configuration["AppConfig:Endpoint"]), new ManagedIdentityCredential()));
```
## Access stored configurations
To access the stored configurations, define a strongly typed class for the data, and bind the configuration to it.

```csharp
public class Settings { 
	public string BackgroundColor { get; set; } 
	public long FontSize { get; set; } 
	public string FontColor { get; set; } 
	public string Message { get; set; } 
}
```

```csharp
builder.Services.Configure<Settings>(builder.Configuration.GetSection("TestApp:Settings"));
```

The configuration object can then be injected to the target service with the [[Options Pattern]]:

```csharp
public IndexModel(IOptionsSnapshot<Settings> options, ILogger<IndexModel> logger) { Settings = options.Value; _logger = logger; }
```
# Sources
[Use managed identities to access App Configuration](https://learn.microsoft.com/en-us/azure/azure-app-configuration/howto-integrate-azure-managed-service-identity?pivots=framework-dotnet)
[Quickstart: Create an ASP.NET Core app with Azure App Configuration](https://learn.microsoft.com/en-us/azure/azure-app-configuration/quickstart-dotnet-core-app?tabs=windowscommandprompt)