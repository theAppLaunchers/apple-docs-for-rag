

- Apple CryptoKit
- HPKE
- HPKE.Recipient
-  init(privateKey:ciphersuite:info:encapsulatedKey:authenticatedBy:presharedKey:presharedKeyIdentifier:) 

Initializer

# init(privateKey:ciphersuite:info:encapsulatedKey:authenticatedBy:presharedKey:presharedKeyIdentifier:)

Creates a recipient in authentication and preshared key mode.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+tvOS 17.0+visionOS 1.0+watchOS 10.0+

``` source
init(
    privateKey: SK,
    ciphersuite: HPKE.Ciphersuite,
    info: Data,
    encapsulatedKey: Data,
    authenticatedBy authenticationKey: SK.PublicKey,
    presharedKey psk: SymmetricKey,
    presharedKeyIdentifier pskID: Data
) throws where SK : HPKEDiffieHellmanPrivateKey
```

## Parameters 

`privateKey`  

The recipient’s private key for decrypting the incoming messages.

`ciphersuite`  

The cipher suite that defines the cryptographic algorithms to use.

`info`  

Data that the key derivation function uses to compute the symmetric key material. The sender and the recipient need to use the same `info` data.

`encapsulatedKey`  

The encapsulated symmetric key that the sender provides.

`authenticationKey`  

The sender’s public key for authenticating the messages.

`psk`  

A preshared key (PSK) that the sender and the recipient both hold.

`pskID`  

An identifier for the PSK.

## Discussion

The `Receiver` decrypts messages it receives in authentication and preshared key (`auth_psk`) mode using the encapsulated key with the key schedule information (`info` data), in addition to a symmetric encryption key that the sender and recipient both know in advance. Messages also include authentication data so that the recipient can verify the authenticity of the sender’s private key.

Note

The system throws errors from HPKE.Errors when it encounters them.

