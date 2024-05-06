# OpenID Connect

## OAuth2 Terminology

| Name | Description | Link |
|--|--|--|
| JSON Web Signature (JWS) | | https://datatracker.ietf.org/doc/html/rfc7515 |
| JSON Web Token (JWT) | JWT (JSON Web Token) is a JSON-format object for securely transferring claims between two parties as defined by open standards. JWT consists of three separate Base64-encoded parts: <ul><li>JOSE Header - The type of token and the algorithm used in the signature</li><li>JWS Payload - A set of claims describing the user's identity and privileges</li><li>JWS Signature - The signature used to ensure the integrity and correctness of the token, to be verified</li></ul> | https://auth0.com/docs/secure/tokens/json-web-tokens |
| JSON Web Key Sets (JWKS) | JWKS (JSON Web Key Sets) is a JSON-based standard for publishing and sharing public keys in web applications. It is part of the JSON Web Token (JWT) ecosystem and helps ensure the integrity of digitally signed or encrypted messages. <br><br> JWKS contains one or more keys (JSON Web Keys), and each key's details are specified using standardized fields, such as: <ul><li>`kty` (key type)</li><li>`use` (key use)</li><li>`alg` (algorithm)</li><li>`kid` (key ID)</li></ul> | https://auth0.com/docs/secure/tokens/json-web-tokens/json-web-key-sets |

## Token types

### Id token

### Access token