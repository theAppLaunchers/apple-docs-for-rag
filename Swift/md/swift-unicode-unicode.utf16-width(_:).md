

- Swift
- Unicode
- Unicode.UTF16
-  width(\_:) 

Type Method

# width(\_:)

Returns the number of code units required to encode the given Unicode scalar.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
static func width(_ x: Unicode.Scalar) -> Int
```

## Parameters 

`x`  

A Unicode scalar value.

## Return Value

The width of `x` when encoded in UTF-16, either `1` or `2`.

## Discussion

Because a Unicode scalar value can require up to 21 bits to store its value, some Unicode scalars are represented in UTF-16 by a pair of 16-bit code units. The first and second code units of the pair, designated *leading* and *trailing* surrogates, make up a *surrogate pair*.

```
let anA: Unicode.Scalar = "A"
print(anA.value)
// Prints "65"
print(UTF16.width(anA))
// Prints "1"

let anApple: Unicode.Scalar = "🍎"
print(anApple.value)
// Prints "127822"
print(UTF16.width(anApple))
// Prints "2"
```

