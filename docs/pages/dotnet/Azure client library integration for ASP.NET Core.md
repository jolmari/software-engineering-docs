https://learn.microsoft.com/en-us/dotnet/api/overview/azure/microsoft.extensions.azure-readme?view=azure-dotnet

# Installation
The ASP.NET Core integration library is a part of the `Microsoft.Extensions.Azure` NuGet package.
```
> dotnet add package Microsoft.Extensions.Azure
```
# Register clients to DI
```csharp
public void ConfigureServices(IServiceCollection services) {  
	services.AddAzureClients(builder => { 
		builder
			.AddSecretClient(new Uri("http://my.keyvault.com"))
			.WithName("NamedBlobClient")
			.WithCredential(new ClientSecretCredential("<tenant_id>", "<client_id>", "<client_secret>")) 
			.ConfigureOptions(options => options.Retry.MaxRetries = 10);	
	});
}
```