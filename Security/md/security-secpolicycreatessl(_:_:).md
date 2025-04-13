

- Security
-  SecPolicyCreateSSL(\_:\_:) 

Function

# SecPolicyCreateSSL(\_:\_:)

Returns a policy object for evaluating SSL certificate chains.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.1+macOS 10.6+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func SecPolicyCreateSSL(
    _ server: Bool,
    _ hostname: CFString?
) -> SecPolicy
```

## Parameters 

`server`  

Specify `true` on the client side to return a policy for SSL server certificates.

`hostname`  

If you specify a value for this parameter, the policy will require the specified value to match the host name in the leaf certificate.

## Return Value

The policy object. In Objective-C, call the CFRelease function to release the object when you are finished with it.

## Mentioned in 

Creating a Trust Object

