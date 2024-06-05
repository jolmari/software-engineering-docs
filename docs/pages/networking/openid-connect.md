%% #-🪴weedy %%
[[Unsorted]]
# OpenID Connect

## OAuth2 Terminology

| Name                     | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | Link                                                                   |
| ------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| JSON Web Signature (JWS) |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        | https://datatracker.ietf.org/doc/html/rfc7515                          |
| JSON Web Token (JWT)     | JWT (JSON Web Token) is a JSON-format object for securely transferring claims between two parties as defined by open standards. JWT consists of three separate Base64-encoded parts: <ul><li>JOSE Header - The type of token and the algorithm used in the signature</li><li>JWS Payload - A set of claims describing the user's identity and privileges</li><li>JWS Signature - The signature used to ensure the integrity and correctness of the token, to be verified</li></ul>     | https://auth0.com/docs/secure/tokens/json-web-tokens                   |
| JSON Web Key Sets (JWKS) | JWKS (JSON Web Key Sets) is a JSON-based standard for publishing and sharing public keys in web applications. It is part of the JSON Web Token (JWT) ecosystem and helps ensure the integrity of digitally signed or encrypted messages. <br><br> JWKS contains one or more keys (JSON Web Keys), and each key's details are specified using standardized fields, such as: <ul><li>`kty` (key type)</li><li>`use` (key use)</li><li>`alg` (algorithm)</li><li>`kid` (key ID)</li></ul> | https://auth0.com/docs/secure/tokens/json-web-tokens/json-web-key-sets |

## Token structure

The token structure is described in the official [jwt.io](https://jwt.io/introduction) documentation. The token is formed
of three parts: _header_, _payload_, and _signature_. These parts are combined together to form a token separated by dots `.` to form the following format: `header.payload.signature (xxxxx.yyyyy.zzzzz)`.

### Header

### Payload

### Signature

## Signing algorithms

Signing algorithms are algorithms used to sign tokens issued for your application or API. A signature is part of a JSON Web Token (JWT) and is used to verify that the sender of the token is who it says it is and to ensure that the message wasn't changed along the way.

[OAuth0 - Signing Algorithms](https://auth0.com/docs/get-started/applications/signing-algorithms)

### RS256

RS256 (RSA Signature with SHA-256): An asymmetric algorithm, which means that there are two keys: one public key and one private key that must be kept secret.

### HS256

HS256 (HMAC with SHA-256): A symmetric algorithm, which means that there is only one private key that must be kept secret, and it is shared between the two parties. Since the same key is used both to generate the signature and to validate it, care must be taken to ensure that the key is not compromised.

