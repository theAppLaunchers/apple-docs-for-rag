

- Swift
- UInt16
-  !=(\_:\_:) 

Operator

# !=(\_:\_:)

Returns a Boolean value indicating whether the two given values are not equal.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
static func != (lhs: Self, rhs: Other) -> Bool where Other : BinaryInteger
```

## Parameters 

`lhs`  

An integer to compare.

`rhs`  

Another integer to compare.

## Discussion

You can check the inequality of instances of any `BinaryInteger` types using the not-equal-to operator (`!=`). For example, you can test whether the first `UInt8` value in a string’s UTF-8 encoding is not equal to the first `UInt32` value in its Unicode scalar view:

```
let gameName = "Red Light, Green Light"
if let firstUTF8 = gameName.utf8.first,
    let firstScalar = gameName.unicodeScalars.first?.value {
    print("First code values are different: \(firstUTF8 != firstScalar)")
}
// Prints "First code values are different: false"
```

