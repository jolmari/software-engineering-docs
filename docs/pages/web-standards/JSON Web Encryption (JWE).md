%% #-☢️cryptography  %%
[[Glossary of JSON-based standards]]
# Terminology 
1. `alg` (Algorithm): "alg" refers to the algorithm used to encrypt the key itself or, more precisely, the Content Encryption Key (CEK). When encrypting the payload of a JWT, a symmetric key (the CEK) is generated and used for encryption. However, this key also needs to be securely transmitted to the recipient. To protect the CEK during transit, it is encrypted using the recipient's public key or a shared secret, depending on the key management algorithm specified by "alg." This is often referred to as key wrapping because the key (CEK) is being "wrapped" with another layer of encryption.
    
    The "alg" parameter can have several different values, such as:

    - RSA1_5 or RSA-OAEP: These algorithms use RSA to encrypt the CEK with the recipient's public key.
    - A128KW, A192KW, or A256KW: These algorithms use AES in Key Wrap mode with a specified key size to encrypt the CEK with a shared secret.
2. `enc` (Encryption Algorithm): The "enc" parameter specifies the algorithm used to encrypt the actual JWT payload (the claims) using the CEK. Examples of "enc" values include:
    
    - A128CBC-HS256: AES in CBC mode with a 128-bit key and HMAC-SHA-256 authentication.
    - A192CBC-HS384: AES in CBC mode with a 192-bit key and HMAC-SHA-384 authentication.
    - A256CBC-HS512: AES in CBC mode with a 256-bit key and HMAC-SHA-512 authentication.
    - A128GCM, A192GCM, or A256GCM: AES in GCM mode with a specified key size.