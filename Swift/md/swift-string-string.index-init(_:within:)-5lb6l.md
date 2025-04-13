

- Swift
- String
- String.Index
-  init(\_:within:) 

Initializer

# init(\_:within:)

Creates an index in the given UTF-8 view that corresponds exactly to the specified `UTF16View` position.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
init?(
    _ idx: String.Index,
    within target: String.UTF8View
)
```

## Parameters 

`idx`  

A position in a `String` or one of its views.

`target`  

The `UTF8View` in which to find the new position.

## Discussion

The following example finds the position of a space in a string’s `utf16` view and then converts that position to an index in the string’s `utf8` view.

```
let cafe = "Café 🍵"

let utf16Index = cafe.utf16.firstIndex(of: 32)!
let utf8Index = String.UTF8View.Index(utf16Index, within: cafe.utf8)!

print(Array(cafe.utf8[..

If the position passed in `utf16Index` doesn’t have an exact corresponding position in `utf8`, the result of the initializer is `nil`. For example, because UTF-8 and UTF-16 represent high Unicode code points differently, an attempt to convert the position of the trailing surrogate of a UTF-16 surrogate pair fails.

The next example attempts to convert the indices of the two UTF-16 code points that represent the teacup emoji (`"🍵"`). The index of the lead surrogate is successfully converted to a position in `utf8`, but the index of the trailing surrogate is not.

```
let emojiHigh = cafe.utf16.index(after: utf16Index)
print(String.UTF8View.Index(emojiHigh, within: cafe.utf8))
// Prints "Optional(String.Index(...))"

let emojiLow = cafe.utf16.index(after: emojiHigh)
print(String.UTF8View.Index(emojiLow, within: cafe.utf8))
// Prints "nil"
```

