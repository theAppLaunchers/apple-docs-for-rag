

- Swift
- Unicode
- Unicode.Scalar
- Unicode.Scalar.Properties
-  isDiacritic 

Instance Property

# isDiacritic

A Boolean value indicating whether the scalar is a diacritic.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
var isDiacritic: Bool { get }
```

## Discussion

Diacritics are scalars that linguistically modify the meaning of another scalar to which they apply. Scalars for which this property is `true` are frequently, but not always, combining marks or modifiers.

This property corresponds to the “Diacritic” property in the Unicode Standard.

