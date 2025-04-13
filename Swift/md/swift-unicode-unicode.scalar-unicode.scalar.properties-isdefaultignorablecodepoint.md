

- Swift
- Unicode
- Unicode.Scalar
- Unicode.Scalar.Properties
-  isDefaultIgnorableCodePoint 

Instance Property

# isDefaultIgnorableCodePoint

A Boolean value indicating whether the scalar is a default-ignorable code point.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
var isDefaultIgnorableCodePoint: Bool { get }
```

## Discussion

Default-ignorable code points are those that should be ignored by default in rendering (unless explicitly supported). They have no visible glyph or advance width in and of themselves, although they may affect the display, positioning, or adornment of adjacent or surrounding characters.

This property corresponds to the “Default_Ignorable_Code_Point” and the “Other_Default_Ignorable_Code_point” properties in the Unicode Standard.

