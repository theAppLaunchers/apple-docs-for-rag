

- Swift
- Unicode
- Unicode.Scalar
- Unicode.Scalar.Properties
-  isIDSTrinaryOperator 

Instance Property

# isIDSTrinaryOperator

A Boolean value indicating whether the scalar is an ideographic description character that determines how the three ideographic characters or ideographic description sequences that follow it are to be combined to form a single character.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
var isIDSTrinaryOperator: Bool { get }
```

## Discussion

Ideographic description characters are technically printable characters, but advanced rendering engines may use them to approximate ideographs that are otherwise unrepresentable.

This property corresponds to the “IDS_Trinary_Operator” property in the Unicode Standard.

