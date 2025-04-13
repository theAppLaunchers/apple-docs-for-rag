

- Security
- Certificate, Key, and Trust Services
- Trust
-  Evaluating a Trust and Parsing the Result 

Article

# Evaluating a Trust and Parsing the Result

Learn what to expect when evaluating a trust object.

## Overview

Using the trust object that you obtained in Creating a Trust Object, you evaluate it with the SecTrustEvaluateAsyncWithError(_:_:_:) method:

- Swift
- Objective-C

```
DispatchQueue.global().async {
    SecTrustEvaluateAsyncWithError(trust, DispatchQueue.global()) {
        trust, result, error in

        if result {
            let publicKey = SecTrustCopyPublicKey(trust)

            // Use key . . .
        } else {
            print("Trust failed: \(error!.localizedDescription)")
        }
    }
}
```

```
dispatch_async(dispatch_get_global_queue(DISPATCH_QUEUE_PRIORITY_DEFAULT, 0), ^{
    SecTrustEvaluateAsyncWithError(
        trust,
        dispatch_get_global_queue(DISPATCH_QUEUE_PRIORITY_DEFAULT, 0),
        ^(SecTrustRef evaluatedTrust, bool trustResult, CFErrorRef error) {
            if (trustResult == YES) {
                // Evaluation succeeded!
                SecKeyRef publicKey = SecTrustCopyPublicKey(evaluatedTrust);

                // Use and release key . . .

            } else {
                // Evaluation failed: Check the error
            }

            // Finally, release the trust and error.
            if (evaluatedTrust) { CFRelease(evaluatedTrust); }
            if (error)          { CFRelease(error); }
        }
    );
});
```

If the trust object already has a result, the evaluation might invoke the callback synchronously, before the method returns. In other cases, like when the evaluation needs to fetch intermediate certificates or perform revocation checking, it might instead return immediately, perform the evaluation asynchronously, and call the closure later with a result. Either way, you must call the evaluation method on the same thread that you specify for the closure.

When the evaluation finishes and the method invokes the callback, examine the `result` parameter. If the trust result is `true`, the evaluation succeeded. At this point, you can get the public key from the leaf certificate with SecTrustCopyPublicKey(_:), as explained in Getting an Existing Key, and begin to use it. If the result is `false`, you might be able to recover from the failure, as described in Discovering Why a Trust Evaluation Failed. If you can’t recover—for example, because the certificate is revoked—handle the failure gracefully.

