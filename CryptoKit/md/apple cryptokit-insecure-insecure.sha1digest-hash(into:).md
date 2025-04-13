

- Apple CryptoKit
- Insecure
- Insecure.SHA1Digest
-  hash(into:) 

Instance Method

# hash(into:)

Hashes the essential components of the digest by feeding them into the given hash function.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
func hash(into hasher: inout Hasher)
```

## Parameters 

`hasher`  

The hash function to use when combining the components of the digest.

## Discussion

This method is part of the digest’s conformance to Swift standard library’s Hashable protocol, making it possible to compare digests. Don’t confuse that hashing with the cryptographically secure hashing that you use to create the digest in the first place by, for example, calling `Insecure/SHA1/hash(data:)`.

