[[IdentityModel]]
[[JWE tokens with IdentityModel]]
[[JWT tokens with IdentityModel]]
[[Glossary of JSON-based standards]]
# Description
When using Azure Key Vault stored keys, regardless of software or HSM based, the private key pair of the asymmetric key should not leak out of the vault. In the case of HSM keys, this is not even possible.

The signing and decrypting of JWS and JWE requires access to the private key through `SigningCredentials` or `EncryptingCredentials`. As there is no built-in mechanism to provide these automatically, and the `KeyVaultExtensions`-option does not support encryption, this requires custom code.
## Why not use the official KeyVaultExtensions-library
There are some problems in the implementation of the official extensions library:
- There is support for Key Vault based `SigningCredentials`, but no direct support for `EncryptingCredentials`
- The [KeyVaultSecurityKey](https://github.com/AzureAD/azure-activedirectory-identitymodel-extensions-for-dotnet/blob/dc15328457df098e157363713fc5d32724458c72/src/Microsoft.IdentityModel.KeyVaultExtensions/KeyVaultSecurityKey.cs)-implementation creates its own client, which makes it hard to test.
- There are bugs related to using the recommended `JsonWebTokens` library. These prevent the using of Key Vaylt providers. https://github.com/AzureAD/azure-activedirectory-identitymodel-extensions-for-dotnet/issues/2231
## IdentityModel cryptography extensibility
`IdentityModel` offers an interface that can be implemented if there is a need for custom cryptography functionality. The approach to using key vault signatures and encryption will follow these steps:
1. Create `KeyVaultCryptoProvider` implementation of `ICryptoProvider`
2. Override supported algorithms in `IsSupportedAlgorithm`
3. Override and implement algorithm specific operations in `Create`
	1. Implement custom `SignatureProvider` for key vault
	2. Implement custom `KeyWrapProvider` for key vault
	3. Implement custom `AsymmetricSecurityKey` for key vault
Some of this functionality can (and will) be copied from the GitHub-repository: https://github.com/AzureAD/azure-activedirectory-identitymodel-extensions-for-dotnet/wiki/Keyvault-extensions
## Add keys to Key Vault
Follow the instructions to set correct RBAC permissions, and the keys to the Key Vault. [[keyvault]]
# Custom Key Vault crypto provider 
The following custom parts form the Key Vault cryptography toolkit:
## Key Vault Crypto Provider
The `CryptoProvider`-class is used as a branching point between different Key Vault operations. The provider selects the underlying provider based on the algorithm type.

https://github.com/jolmari/azure-cli-scripts/blob/main/dotnet/dotnet-jwt-security-token/JwtSecurityTokenSamples/KeyVault/KeyVaultCryptoProvider.cs

```csharp
public class KeyVaultCryptoProvider : ICryptoProvider  {
...
}
```
## Key Vault Signature Provider
https://github.com/jolmari/azure-cli-scripts/blob/main/dotnet/dotnet-jwt-security-token/JwtSecurityTokenSamples/KeyVault/KeyVaultSignatureProvider.cs
```csharp
public class KeyVaultKeySignatureProvider : SignatureProvider {
...
}
```
## Key Vault Key Wrap Provider
https://github.com/jolmari/azure-cli-scripts/blob/main/dotnet/dotnet-jwt-security-token/JwtSecurityTokenSamples/KeyVault/KeyVaultKeyWrapProvider.cs
```csharp
public class KeyVaultKeyWrapProvider : KeyWrapProvider {
...
}
```
## Key Vault based RSA Security Key
https://github.com/jolmari/azure-cli-scripts/blob/main/dotnet/dotnet-jwt-security-token/JwtSecurityTokenSamples/KeyVault/KeyVaultRsaSecurityKey.cs
## Decryption
```csharp
var signingKey = await keyClient.GetKeyAsync("TestSigningKey", "c1d4752f020b4a77a9c899901db7c7cd");
var signingRsaKey = new KeyVaultRsaSecurityKey(signingKey)
{
	CryptoProviderFactory = cryptoProviderFactory
};
```
## Signing
```csharp
var encryptionKey = await keyClient.GetKeyAsync("TestEncryptionKey", "b073d79dcaa74d7d9c7588a475b4fd91");
var encryptionRsaKey = new KeyVaultRsaSecurityKey(encryptionKey)
{
	CryptoProviderFactory = cryptoProviderFactory
};
```
## Example 
https://gist.github.com/joonaszure/507be31b6213b7daf4ca05c99a201f15