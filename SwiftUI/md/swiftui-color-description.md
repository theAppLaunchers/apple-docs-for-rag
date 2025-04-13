

- SwiftUI
- Color
-  description 

Instance Property

# description

A textual representation of the color.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
var description: String { get }
```

## Discussion

Use this method to get a string that represents the color. The print(_:separator:terminator:) function uses this property to get a string representing an instance:

```
print(Color.red)
// Prints "red"
```

