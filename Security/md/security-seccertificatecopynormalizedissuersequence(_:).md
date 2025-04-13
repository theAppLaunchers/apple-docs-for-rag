

- Security
-  SecCertificateCopyNormalizedIssuerSequence(\_:) 

Function

# SecCertificateCopyNormalizedIssuerSequence(\_:)

Retrieves the normalized issuer sequence from a certificate.

iOS 10.3+iPadOS 10.3+Mac Catalyst 13.1+macOS 10.12.4+tvOS 10.2+visionOS 1.0+watchOS 3.2+

``` source
func SecCertificateCopyNormalizedIssuerSequence(_ certificate: SecCertificate) -> CFData?
```

## Parameters 

`certificate`  

The certificate from which to retrieve the data.

## Return Value

A data object containing the sequence or `NULL` on error. In Objective-C, free this object with a call to the CFRelease function when you are done with it.

