%% #-☢️cryptography  %%
[[JSON Web Encryption (JWE)]]
[[IdentityModel]]s
[[Glossary of JSON-based standards]]

https://github.com/AzureAD/azure-activedirectory-identitymodel-extensions-for-dotnet/wiki/Creating-and-Validating-JWEs-(Json-Web-Encryptions)
# Encryption
An example of encrypting a signed JWT (JWT+JWS) with JWE using IdentityModel:
```csharp
var securityTokenHandler = new JsonWebTokenHandler();  
var encryptingCredentials = new EncryptingCredentials(  
    new X509SecurityKey(encryptionCertificate) {  
       KeyId = "jwe-encryption-key"  
    },  
    SecurityAlgorithms.RsaOAEP,  
    SecurityAlgorithms.Aes128Gcm);  
  
return securityTokenHandler.CreateToken(new SecurityTokenDescriptor {  
    SigningCredentials = x509SigningCredentials,  
    EncryptingCredentials = encryptingCredentials  
});
```
# Sources
## Nuget package
[Microsoft.IdentityModel.JsonWebTokens](https://github.com/AzureAD/azure-activedirectory-identitymodel-extensions-for-dotnet)
## Project
[azure-activedirectory-identitymodel-extensions-for-dotnet](https://github.com/AzureAD/azure-activedirectory-identitymodel-extensions-for-dotnet)
