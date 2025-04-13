

- Swift
- Unicode
- Unicode.Scalar
- Unicode.Scalar.Properties
-  isIDSBinaryOperator 

Instance Property

# isIDSBinaryOperator

A Boolean value indicating whether the scalar is an ideographic description character that determines how the two ideographic characters or ideographic description sequences that follow it are to be combined to form a single character.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
var isIDSBinaryOperator: Bool { get }
```

## Discussion

Ideographic description characters are technically printable characters, but advanced rendering engines may use them to approximate ideographs that are otherwise unrepresentable.

This property corresponds to the “IDS_Binary_Operator” property in the Unicode Standard.

