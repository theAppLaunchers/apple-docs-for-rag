

- Security
-  SecTrustGetVerifyTime(\_:) 

Function

# SecTrustGetVerifyTime(\_:)

Gets the absolute time against which the certificates in a trust management object are verified.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.1+macOS 10.6+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func SecTrustGetVerifyTime(_ trust: SecTrust) -> CFAbsoluteTime
```

## Parameters 

`trust`  

The trust management object whose verification time you want to get. A trust management object includes one or more certificates plus the policy or policies to be used in evaluating trust. Use the SecTrustCreateWithCertificates(_:_:_:) function to create a trust management object.

## Return Value

The absolute time at which the certificates should be checked for validity.

## Discussion

This function returns the absolute time returned by:

1.  the CFDateGetAbsoluteTime(_:) function for the date passed in to the SecTrustSetVerifyDate(_:_:) function, if that was called, or

2.  the last value returned by the SecTrustGetVerifyTime(_:) function, if it was called before, or

3.  the value returned by the CFAbsoluteTimeGetCurrent() function if neither SecTrustSetVerifyDate(_:_:) nor SecTrustGetVerifyTime(_:) were ever called.

It is safe to call this function concurrently on two or more threads as long as it is not used to get a value from a trust management object that is simultaneously being changed by another function. For example, you can call this function on two threads at the same time, but not if you are simultaneously calling the SecTrustSetVerifyDate(_:_:) function for the same trust management object on another thread.

## See Also

### Related Documentation

func SecTrustSetVerifyDate(SecTrust, CFDate) -> OSStatus

Sets the date and time against which the certificates in a trust management object are verified.

