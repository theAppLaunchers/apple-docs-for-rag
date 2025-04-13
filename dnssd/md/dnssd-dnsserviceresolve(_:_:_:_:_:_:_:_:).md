

- dnssd
-  DNSServiceResolve(\_:\_:\_:\_:\_:\_:\_:\_:) 

Function

# DNSServiceResolve(\_:\_:\_:\_:\_:\_:\_:\_:)

iOS 10.0+iPadOS 10.0+Mac Catalyst 13.0+macOS 10.12+tvOS 10.0+visionOS 1.0+watchOS 3.0+

``` source
func DNSServiceResolve(
    _ sdRef: UnsafeMutablePointer!,
    _ flags: DNSServiceFlags,
    _ interfaceIndex: UInt32,
    _ name: UnsafePointer!,
    _ regtype: UnsafePointer!,
    _ domain: UnsafePointer!,
    _ callBack: DNSServiceResolveReply!,
    _ context: UnsafeMutableRawPointer!
) -> DNSServiceErrorType
```

## Parameters 

`sdRef`  

A pointer to an uninitialized DNSServiceRef. If the call succeeds then it initializes the DNSServiceRef, returns kDNSServiceErr_NoError, and the resolve operation will run indefinitely until the client terminates it by passing this DNSServiceRef to DNSServiceRefDeallocate(_:).

`flags`  

Specifying kDNSServiceFlagsForceMulticast will cause query to be performed with a link-local mDNS query, even if the name is an apparently non-local name (i.e. a name not ending in “.local.”)

`interfaceIndex`  

The interface on which to resolve the service. If this resolve call is as a result of a currently active DNSServiceBrowse(_:_:_:_:_:_:_:) operation, then the interfaceIndex should be the index reported in the DNSServiceBrowseReply callback. If this resolve call is using information previously saved (e.g. in a preference file) for later use, then use interfaceIndex 0, because the desired service may now be reachable via a different physical interface. See “Constants for specifying an interface index” for more details.

`name`  

The name of the service instance to be resolved, as reported to the DNSServiceBrowseReply callback.

`regtype`  

The type of the service instance to be resolved, as reported to the DNSServiceBrowseReply callback.

`domain`  

The domain of the service instance to be resolved, as reported to the DNSServiceBrowseReply callback.

`callBack`  

The function to be called when a result is found, or if the call asynchronously fails.

`context`  

An application context pointer which is passed to the callback function (may be NULL).

## Return Value

Returns kDNSServiceErr_NoError on success (any subsequent, asynchronous errors are delivered to the callback), otherwise returns an error code indicating the error that occurred (the callback is never invoked and the DNSServiceRef is not initialized).

## See Also

### Service Discovery

func DNSServiceBrowse(UnsafeMutablePointer&lt;DNSServiceRef?>!, DNSServiceFlags, UInt32, UnsafePointer&lt;CChar>!, UnsafePointer&lt;CChar>!, DNSServiceBrowseReply!, UnsafeMutableRawPointer!) -> DNSServiceErrorType

Browses for available services.

