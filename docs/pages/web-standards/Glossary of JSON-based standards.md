# Types of JSON data structures
## JWT (JSON Web Token) 
JWT is a compact, URL-safe means of representing claims between two parties. A JWT by itself doesn't imply any specific encoding or encryption approach. It simply serves as a container for the claims to be transmitted. JWTs can be represented in two forms: either as a JWS, when they are signed, or as a JWE, when they are encrypted.
## JWS (JSON Web Signature) 
JWS is a standard that specifies how to digitally sign or create a message authentication code (MAC) for the contents of the JWT. This provides integrity for the token so that the recipient can verify that the token has not been tampered with. A JWS can be recognized by having two periods that separate the token into three parts: header, payload, and signature (e.g., `xxxxx.yyyyy.zzzzz`).
## JWE (JSON Web Encryption)
JWE is a standard for encrypting the content of the JWT. This means that the claims within the JWT are hidden from anyone who doesn't have the appropriate key to decrypt the content, ensuring the confidentiality of the token's payload. 
### Hybrid encryption
The JWE is encrypted with a form of hybrid encryption. The content itself is encrypted with a symmetric Content Encryption Key (CEK), and the symmetric key is encrypted with public key encryption.

The motivation behind using hybrid encryption is the efficiency of symmetric encryption algorithms compared to asymmetric. It is faster to encrypt the payload of any size with a symmetric algorithm, and then use the asymmetric algorithm to encrypt the small CEK-key.
### Structure
Unlike a JWS, a JWE has five parts separated by periods, corresponding to *header*, *encrypted key*, *initialization vector*, *ciphertext*, and *authentication tag* (e.g., `aaaaa.bbbbb.ccccc.ddddd.eeeee`).
### Header
The base64-encoded header describes the JWE, how it was encrypted, and the media type of the encrypted content.

`"alg"` defines the asymmetric encryption algorithm used to encrypt the CEK.
`"kid"` defines the identifier of the public key used to encrypt the CEK.
`"enc"`: defines the symmetric encryption algorithm used to encrypt the content with the CEK.

```json
{
  "alg": "RSA-OAEP",
  "enc": "A256CBC-HS512",
  "kid": "18b1cf758c1d4ec6bda6589357abdd85",
  "typ": "JWT",
  "cty": "JWT"
}
```
### Encrypted key (CEK)
The CEK is the key used to encrypt the JWE payload. This is the key used during symmetric encryption, itself encrypted using your asymmetric encryption key (RSA-OAEP). The CEK is unique for each token, and must never be re-used.
### Initialization vector (IV)
The initialization vector used when encrypting the plaintext. This must be a unique, random value. If your symmetric encryption algorithm does not require an initialization vector, then this should be an empty octet sequence.
### Ciphertext
The encrypted payload which was encrypted using authenticated encryption thanks to your symmetric encryption algorithm (A256CBC-HS512). This used the JWE’s Content Encryption Key (CEK) as the encryption key, along with the JWE initialization vector and the “Additional Authenticated Data” (AAD), which, when using compact serialization, is the encoded JWE protected header.
### JWE authentication tag
The authentication tag created during authenticated encryption allows the verifier to prove the integrity of the ciphertext and the AAD (the header). This tag is created during encryption and validated as part of decryption.
# Relationship
In certain scenarios, a JWT might be both signed and encrypted:

1. **Signed then Encrypted**: The token is first signed to create a JWS and then the JWS is encrypted to create a JWE. This ensures the token's integrity and then its confidentiality. The recipient first decrypts the token, and then verifies the signature. This is the most common scenario for sending sensitive information while also ensuring that the sender is authenticated.
    
2. **Encrypted then Signed**: The token is first encrypted to create a JWE and then the JWE is signed. This is less common and can make verification of the signature tricky because the recipient must first verify the signature before decrypting the token.
# Sources
[Scott Brady, 2022. Understanding JSON Web Encryption (JWE)](https://www.scottbrady91.com/jose/json-web-encryption)