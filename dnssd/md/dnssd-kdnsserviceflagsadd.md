

- dnssd
-  kDNSServiceFlagsAdd 

Global Variable

# kDNSServiceFlagsAdd

iOS 10.0+iPadOS 10.0+Mac Catalyst 13.0+macOS 10.12+tvOS 10.0+visionOS 1.0+watchOS 3.0+

``` source
var kDNSServiceFlagsAdd: UInt32 { get }
```

## Discussion

Indicates that the domain is newly discovered. If NOT set, indicates a “Remove”, i.e. the domain is no longer valid. Used in domain enumeration and browse/query reply callbacks.

