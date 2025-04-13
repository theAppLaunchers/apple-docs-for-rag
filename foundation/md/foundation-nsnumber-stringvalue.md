

- Foundation
- NSNumber
-  stringValue 

Instance Property

# stringValue

The number object’s value expressed as a human-readable string.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.0+macOS 10.0+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
var stringValue: String { get }
```

## Discussion

The string is created by invoking description(withLocale:) where locale is `nil`.

## See Also

### Retrieving String Representations

func description(withLocale: Any?) -> String

