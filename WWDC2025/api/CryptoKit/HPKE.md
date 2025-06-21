*   [Apple CryptoKit](/documentation/cryptokit)
*   HPKE

Enumeration

# HPKE

A container for hybrid public key encryption (HPKE) operations.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+tvOS 17.0+visionOS 1.0+watchOS 10.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
enum HPKE
```
```
```
```
```
```
```
```

## [Overview](/documentation/CryptoKit/HPKE#overview)

Hybrid public key encryption (HPKE) uses a symmetric encryption algorithm to encrypt data, and encapsulates the symmetric encryption material using a public key encryption algorithm.

HPKE ensures that the ciphertext wasn’t tampered with after its creation. It can also check the validity of additional cleartext data in apps where you need to send headers or other metadata as cleartext.

HPKE optionally incorporates sender authentication, allowing the recipient to validate the authenticity of messages using the sender’s public key.

HPKE is described in the Internet Research Task Force (IRTF) document [RFC 9180](https://www.ietf.org/rfc/rfc9180.pdf).

## [Topics](/documentation/CryptoKit/HPKE#topics)

### [Sending and receiving messages](/documentation/CryptoKit/HPKE#Sending-and-receiving-messages)

```swift
```swift
```swift
```swift
struct Sender
```
```

A type that represents the sending side of an HPKE message exchange.
```
```swift
```swift
```swift
struct Recipient
```
```

A type that represents the receiving side of an HPKE message exchange.
```
```

### [Choosing cryptographic algorithms](/documentation/CryptoKit/HPKE#Choosing-cryptographic-algorithms)

```swift
```swift
```swift
```swift
struct Ciphersuite
```
```

Cipher suites to use in hybrid public key encryption (HPKE).
```
```swift
```swift
```swift
enum AEAD
```
```

The authenticated encryption with associated data (AEAD) algorithms to use in HPKE.
```
```swift
```swift
```swift
enum KDF
```
```

The key derivation functions to use in HPKE.
```
```swift
```swift
```swift
enum KEM
```
```

The key encapsulation mechanisms to use in HPKE.
```
```swift
```swift
```swift
enum DHKEM
```
```

A container for Diffie-Hellman key encapsulation mechanisms (KEMs).
```
```

### [Handling errors](/documentation/CryptoKit/HPKE#Handling-errors)

```swift
```swift
```swift
```swift
enum Errors
```
```

Hybrid public key encryption (HPKE) errors that CryptoKit uses.
```
```

## [Relationships](/documentation/CryptoKit/HPKE#relationships)

### [Conforms To](/documentation/CryptoKit/HPKE#conforms-to)

*   [`Sendable`](/documentation/Swift/Sendable)
*   [`SendableMetatype`](/documentation/Swift/SendableMetatype)

## [See Also](/documentation/CryptoKit/HPKE#see-also)

### [Public key cryptography](/documentation/CryptoKit/HPKE#Public-key-cryptography)

```swift
```swift
```swift
```swift
enum Curve25519
```
```

An elliptic curve that enables X25519 key agreement and Ed25519 signatures.
```
```swift
```swift
```swift
enum P521
```
```

An elliptic curve that enables NIST P-521 signatures and key agreement.
```
```swift
```swift
```swift
enum P384
```
```

An elliptic curve that enables NIST P-384 signatures and key agreement.
```
```swift
```swift
```swift
enum P256
```
```

An elliptic curve that enables NIST P-256 signatures and key agreement.
```
```swift
```swift
```swift
struct SharedSecret
```
```

A key agreement result from which you can derive a symmetric cryptographic key.
```
```swift
```swift
```swift
enum SecureEnclave
```
```

A representation of a device’s hardware-based key manager.
```
```