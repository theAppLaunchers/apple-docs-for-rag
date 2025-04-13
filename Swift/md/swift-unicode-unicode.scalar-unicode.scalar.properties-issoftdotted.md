

- Swift
- Unicode
- Unicode.Scalar
- Unicode.Scalar.Properties
-  isSoftDotted 

Instance Property

# isSoftDotted

A Boolean value indicating whether the scalar has a “soft dot” that disappears when a diacritic is placed over the scalar.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
var isSoftDotted: Bool { get }
```

## Discussion

For example, “i” is soft dotted because the dot disappears when adding an accent mark, as in “í”.

This property corresponds to the “Soft_Dotted” property in the Unicode Standard.

