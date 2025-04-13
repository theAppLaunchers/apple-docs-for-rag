

- Security
-  SecTrustWithErrorCallback 

Type Alias

# SecTrustWithErrorCallback

A block called with the results of an asynchronous trust evaluation.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.0+macOS 10.0+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
typealias SecTrustWithErrorCallback = (SecTrust, Bool, CFError?) -> Void
```

## Parameters 

`trustRef`  

The trust that was evaluated.

`result`  

A Boolean that’s `true` if the certificate is trusted, or `false` if not.

`error`  

An error that indicates the reason for trust failure, if applicable.

## Discussion

Provide a block of this type as the final argument to the SecTrustEvaluateAsyncWithError(_:_:_:) method to receive the result of the trust evaluation.

The block provides a pass or fail indicator and an error describing the reason for any failure. In the case of multiple certificate failures, the error contains a code representing the most serious. The localized description indicates the certificate with the most serious problem and the type of error. The underlying error contains a localized description of each certificate in the chain that had an error and all errors found with that certificate.

