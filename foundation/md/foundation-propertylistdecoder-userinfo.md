

- Foundation
- PropertyListDecoder
-  userInfo 

Instance Property

# userInfo

A dictionary you use to customize decoding by providing contextual information.

iOS 8.0+iPadOS 8.0+Mac Catalyst 8.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
@preconcurrency
var userInfo: [CodingUserInfoKey : any Sendable] { get set }
```

## See Also

### Customizing Decoding

func decode&lt;T>(T.Type, from: Data, format: inout PropertyListDecoder.PropertyListFormat) throws -> T

Returns a value of the specified type by decoding a property list using the supplied format.

