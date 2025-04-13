

- Swift
- String
- String.Index
-  init(\_:within:) 

Initializer

# init(\_:within:)

Creates an index in the given string that corresponds exactly to the specified position.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
init?(
    _ sourcePosition: String.Index,
    within target: S
) where S : StringProtocol
```

## Parameters 

`sourcePosition`  

A position in a view of the `target` parameter. `sourcePosition` must be a valid index of at least one of the views of `target`.

`target`  

The string referenced by the resulting index.

## Discussion

If the index passed as `sourcePosition` represents the start of an extended grapheme cluster—the element type of a string—then the initializer succeeds.

The following example converts the position of the Unicode scalar `"e"` into its corresponding position in the string. The character at that position is the composed `"é"` character.

```
let cafe = "Cafe\u{0301}"
print(cafe)
// Prints "Café"

let scalarsIndex = cafe.unicodeScalars.firstIndex(of: "e")!
let stringIndex = String.Index(scalarsIndex, within: cafe)!

print(cafe[...stringIndex])
// Prints "Café"
```

If the index passed as `sourcePosition` doesn’t have an exact corresponding position in `target`, the result of the initializer is `nil`. For example, an attempt to convert the position of the combining acute accent (`"\u{0301}"`) fails. Combining Unicode scalars do not have their own position in a string.

```
let nextScalarsIndex = cafe.unicodeScalars.index(after: scalarsIndex)
let nextStringIndex = String.Index(nextScalarsIndex, within: cafe)

print(nextStringIndex)
// Prints "nil"
```

