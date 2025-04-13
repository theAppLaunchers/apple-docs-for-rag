

- Apple CryptoKit
- HPKE
- HPKE.Sender
-  init(recipientKey:ciphersuite:info:authenticatedBy:) 

Initializer

# init(recipientKey:ciphersuite:info:authenticatedBy:)

Creates a sender in authentication mode.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+tvOS 17.0+visionOS 1.0+watchOS 10.0+

``` source
init(
    recipientKey: SK.PublicKey,
    ciphersuite: HPKE.Ciphersuite,
    info: Data,
    authenticatedBy authenticationKey: SK
) throws where SK : HPKEDiffieHellmanPrivateKey
```

## Parameters 

`recipientKey`  

The recipient’s public key for encrypting the messages.

`ciphersuite`  

The cipher suite that defines the cryptographic algorithms to use.

`info`  

Data that the key derivation function uses to compute the symmetric key material. The sender and the recipient need to use the same `info` data.

`authenticationKey`  

The sender’s private key for generating the HMAC.

## Discussion

The `Sender` encrypts messages in authentication mode with a symmetric encryption key. Messages also include authentication data so that the recipient can verify the authenticity of the sender’s private key.

Note

The system throws errors from HPKE.Errors when it encounters them.

