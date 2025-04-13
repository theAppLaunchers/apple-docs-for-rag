

- Apple CryptoKit
- HPKE
- HPKE.Recipient
-  init(privateKey:ciphersuite:info:encapsulatedKey:presharedKey:presharedKeyIdentifier:) 

Initializer

# init(privateKey:ciphersuite:info:encapsulatedKey:presharedKey:presharedKeyIdentifier:)

Creates a recipient in preshared key (PSK) mode.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+tvOS 17.0+visionOS 1.0+watchOS 10.0+

``` source
init(
    privateKey: SK,
    ciphersuite: HPKE.Ciphersuite,
    info: Data,
    encapsulatedKey: Data,
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

`psk`  

A preshared key (PSK) that the sender and the recipient both hold.

`pskID`  

An identifier for the PSK.

## Discussion

The `Receiver` decrypts messages in PSK mode using the encapsulated key with the key schedule information (`info` data), in addition to a symmetric encryption key that the sender and recipient both know in advance.

Note

The system throws errors from HPKE.Errors when it encounters them.

