%% #-🪴weedy %%
[[Unsorted]]
# Keyvault

## Standard

## Premium 

###  Hardware Security Module (HSM)

Hardware Security Module (HSM) is a physical device that safeguards and manages digital keys for strong authentication and provides cryptoprocessing. Creating a HSM enabled key in Keyvault is possible by selecting either `RSA-SHM` or `RSA-EC` option when creating a new key in the premium keyvault.

#### CLI - Create a RSA-HSM key, 4096 bits

```sh
> az keyvault key create --name "<key-name>" --vault-name "<premium-keyvault-name>" --kty "RSA-HSM" --size 4096 --protection "hsm"
```

#### RBAC permissions

The `Key Vault Contributor` role gives access only to the control plane level of the keyvault. In order to manage keys,
the user requires `Key Vault Administrator` or `Key Vault Crypto Officer` role.

### Sign a JWT with a HSM key in .NET

### Validate the signature of a JWT in .NET

## References

1. [Microsoft (2024), Create an RSA key][1]
2. [Microsoft (2024), Zero Trust][2]

[1]: https://learn.microsoft.com/en-us/azure/key-vault/managed-hsm/key-management#create-an-hsm-key
[2]: https://learn.microsoft.com/en-us/security/zero-trust/zero-trust-overview