

- Apple CryptoKit
- P256
- P256.Signing
- P256.Signing.PublicKey
-  isValidSignature(\_:for:) 

Instance Method

# isValidSignature(\_:for:)

Verifies an elliptic curve digital signature algorithm (ECDSA) signature on a digest over the P-256 elliptic curve.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
func isValidSignature(
    _ signature: P256.Signing.ECDSASignature,
    for digest: D
) -> Bool where D : Digest
```

## Parameters 

`signature`  

The signature to verify.

`digest`  

The signed digest.

## Return Value

A Boolean value that’s `true` if the signature is valid for the given digest; otherwise, `false`.

## See Also

### Verifying a signature

func isValidSignature&lt;D>(P256.Signing.ECDSASignature, for: D) -> Bool

Verifies an elliptic curve digital signature algorithm (ECDSA) signature on a block of data over the P-256 elliptic curve.

struct ECDSASignature

A P-256 elliptic curve digital signature algorithm (ECDSA) signature.

