

- Swift
- String
-  count 

Instance Property

# count

The number of characters in a string.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
var count: Int { get }
```

## Discussion

To check whether a string is empty, use its `isEmpty` property instead of comparing `count` to zero.

Complexity

O(n), where n is the length of the string.

## See Also

### Inspecting a String

var isEmpty: Bool

A Boolean value indicating whether a string has no characters.

