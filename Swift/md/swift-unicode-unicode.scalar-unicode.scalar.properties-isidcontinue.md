

- Swift
- Unicode
- Unicode.Scalar
- Unicode.Scalar.Properties
-  isIDContinue 

Instance Property

# isIDContinue

A Boolean value indicating whether the scalar is one which is recommended to be allowed to appear in a non-starting position in a programming language identifier.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
var isIDContinue: Bool { get }
```

## Discussion

Applications that store identifiers in NFKC normalized form should instead use `isXIDContinue` to check whether a scalar is a valid identifier character.

This property corresponds to the “ID_Continue” and the “Other_ID_Continue” properties in the Unicode Standard.

