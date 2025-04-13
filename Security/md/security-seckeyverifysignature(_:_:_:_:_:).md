

- Security
-  SecKeyVerifySignature(\_:\_:\_:\_:\_:) 

Function

# SecKeyVerifySignature(\_:\_:\_:\_:\_:)

Verifies the cryptographic signature of a block of data using a public key and specified algorithm.

iOS 10.0+iPadOS 10.0+Mac Catalyst 13.1+macOS 10.12+tvOS 10.0+visionOS 1.0+watchOS 3.0+

``` source
func SecKeyVerifySignature(
    _ key: SecKey,
    _ algorithm: SecKeyAlgorithm,
    _ signedData: CFData,
    _ signature: CFData,
    _ error: UnsafeMutablePointer?>?
) -> Bool
```

## Parameters 

`key`  

The public key to use in evaluating the signature.

`algorithm`  

The algorithm that was used to create the signature. Use one of the signing algorithms listed in SecKeyAlgorithm. You can use the SecKeyIsAlgorithmSupported(_:_:_:) function to test that the key is suitable for the algorithm.

`signedData`  

The data that was signed.

`signature`  

The signature that was created with a call to the SecKeyCreateSignature(_:_:_:_:) function.

`error`  

The address of a doc://com.apple.documentation/documentation/corefoundation/cferror-ru8 object. If an error occurs, this is set to point at an error instance that describes the failure.

## Return Value

A Boolean indicating whether or not the data and signature are intact.

## Mentioned in 

Signing and Verifying

