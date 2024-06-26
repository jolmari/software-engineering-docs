%% #-☢️cryptography  %%
[[Glossary of JSON-based standards]]
[[IdentityModel]]

# Use cases
## Override the `typ`-header claim
Overriding the token `typ` header claim (default "JWT") is possible by initializing a `SecurityTokenDescriptor`-class instance with the `AdditionalHeaders`-property. Assign a `typ`-claim.

```csharp
var securityTokenDescriptor = new SecurityTokenDescriptor {  
    Issuer = issuer,  
    Claims = claims,  
    Expires = expiresOn.UtcDateTime,  
    AdditionalHeaderClaims = new Dictionary<string, object> {  
       { "typ", "entity-statement+-jwt" }  
    }  
};
```

https://learn.microsoft.com/en-us/dotnet/api/microsoft.identitymodel.tokens.securitytokendescriptor.tokentype?view=msal-web-dotnet-latest
# Best practices
## Checking for token validity
https://github.com/AzureAD/azure-activedirectory-identitymodel-extensions-for-dotnet/wiki/ValidatingTokens#negative-testing-with-unit-test-andor-e2e-testing
## Important negative testing scenarios
https://github.com/AzureAD/azure-activedirectory-identitymodel-extensions-for-dotnet/wiki/ValidatingTokens#negative-testing-with-unit-test-andor-e2e-testing
# Examples

## Validating JWTs with JsonWebTokenHandler
https://github.com/AzureAD/azure-activedirectory-identitymodel-extensions-for-dotnet/wiki/ValidatingTokens
# Sources
## Nuget package
[Microsoft.IdentityModel.JsonWebTokens](https://github.com/AzureAD/azure-activedirectory-identitymodel-extensions-for-dotnet)
## Project
[azure-activedirectory-identitymodel-extensions-for-dotnet](https://github.com/AzureAD/azure-activedirectory-identitymodel-extensions-for-dotnet)
