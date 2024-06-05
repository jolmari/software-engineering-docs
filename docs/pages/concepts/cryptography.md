%% #-🪴weedy %%
[[Unsorted]]
# Cryptography

## Symmetric vs Asymmetric Cryptography

Cryptography is the practice of securing communication and data in such a way that only the intended recipient can access it. There are two main types of cryptography: symmetric and asymmetric.

### Symmetric Cryptography

Symmetric cryptography uses a _single key_ to encrypt and decrypt data. The same key is used for both encryption and decryption. This key must be kept secret, as anyone who has access to it can decrypt the data. Examples of symmetric encryption algorithms include AES, DES, and 3DES.

### Asymmetric Cryptography

Asymmetric cryptography uses two keys: _a public key_ and _a private key_. The public key is used to encrypt data, while the private key is used to decrypt it. The public key can be shared with anyone, while the private key must be kept secret. Examples of asymmetric encryption algorithms include RSA, DSA, and ECC.

## Digital encryption and signing

### Digital signing

Cryptographic digital signatures use cryptographic algorithms to provide data integrity. The data issuer digitally signs the data by using a private key of a asymmetric key-pair. Anyone who has access to the public key pair can verify the signature. This signature validation is performed to verify that the data was sent issuer, and it has not been tampered with during transport.

### Digital encryption

Digital encryption is the process of converting plaintext data into ciphertext data using a cryptographic algorithm and a key. The ciphertext data can only be decrypted using the corresponding decryption key. This process ensures that only the intended recipient can access the data.

#### Public key encryption

Public key encryption is a type of asymmetric encryption that uses a pair of keys: a public key and a private key. The public key is used to encrypt data, while the private key is used to decrypt it. This allows anyone to encrypt data using the public key, but only the recipient with the private key can decrypt it.

#### Symmetric key encryption

Symmetric key encryption uses a single key to encrypt and decrypt data. This key must be kept secret, as anyone who has access to it can decrypt the data. Examples of symmetric encryption algorithms include AES, DES, and 3DES.

### Public key certificates

A public key certificate (digital certificate, identity certificate) is an electronic document used to prove the validity
of a public key. The certificate includes the public key, key metadata, information of the owner, and the digital signature of the certificate authority (CA) that issued it.

#### X.509

`X.509` is a standard format for public key certificates.

#### PKCS#7

#### PKCS#12

`PKSC#12` is a standard format for storing a private key and its X.509 public key certificate chain in a single file.

### Encoding types

#### DER

[DER (Distinguished Encoding Rules)](https://docs.fileformat.com/web/der/) is a binary encoding format for X.509 certificates.

#### PEM

[PEM (Privacy Enhanced Mail)](https://en.wikipedia.org/wiki/Privacy-Enhanced_Mail#:~:text=pem%22%20file.,with%20BEGIN%20and%20END%20lines%22.) is another commonly used format for encoding X.509 certificates. It is basically a Base64 encoded DER-file that contains the certificate between `-----BEGIN CERTIFICATE-----` and `-----END CERTIFICATE-----` tags.

```plaintext
-----BEGIN CERTIFICATE-----
MIIDITCCAgmgAwIBAgIUIfZz7
-----END CERTIFICATE-----
```

### Libraries

#### Bouncy Castle

[Bouncy Castle](https://www.bouncycastle.org/) is a Java library that provides cryptographic APIs for Java and C#.
The library can be used to generate key pairs, sign and verify data, encrypt and decrypt data, and work with X.509 certificates. This is useful for example when working with PEM and DER encoded certificates.