

- Swift
- String
- String.Index
-  samePosition(in:) 

Instance Method

# samePosition(in:)

Returns the position in the given string that corresponds exactly to this index.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func samePosition(in characters: String) -> String.Index?
```

## Parameters 

`characters`  

The string to use for the index conversion. This index must be a valid index of at least one view of `characters`.

## Return Value

The position in `characters` that corresponds exactly to this index. If this index does not have an exact corresponding position in `characters`, this method returns `nil`. For example, an attempt to convert the position of a UTF-8 continuation byte returns `nil`.

## Discussion

This example first finds the position of a space (UTF-8 code point `32`) in a string’s `utf8` view and then uses this method find the same position in the string.

```
let cafe = "Café 🍵"
let i = cafe.unicodeScalars.firstIndex(of: "🍵")!
let j = i.samePosition(in: cafe)!
print(cafe[j...])
// Prints "🍵"
```

