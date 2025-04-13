

- Swift
- KeyedDecodingContainerProtocol
-  allKeys 

Instance Property

# allKeys

All the keys the `Decoder` has for this container.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
var allKeys: [Self.Key] { get }
```

**Required**

## Discussion

Different keyed containers from the same `Decoder` may return different keys here; it is possible to encode with multiple key types which are not convertible to one another. This should report all keys present which are convertible to the requested type.

