

- Core Media
-  kCMTextMarkupAttribute_CharacterBackgroundColorARGB 

Global Variable

# kCMTextMarkupAttribute_CharacterBackgroundColorARGB

A background color for individual text characters.

iOS 7.0+iPadOS 7.0+Mac Catalyst 13.1+macOS 10.9+tvOS 9.0+visionOS 1.0+watchOS 6.0+

``` source
let kCMTextMarkupAttribute_CharacterBackgroundColorARGB: CFString
```

## Discussion

This attribute’s value must be a `CFArray` of four `CFNumber`s representing alpha, red, green, and blue fields with values between `0.0` and `1.0`. The system interprets the red, green, and blue components in the sRGB color space. The alpha indicates the opacity from `0.0` for transparent to `1.0` for 100 percent opaque.

## See Also

### Colors

let kCMTextMarkupAttribute_ForegroundColorARGB: CFString

A foreground color for the text.

let kCMTextMarkupAttribute_BackgroundColorARGB: CFString

A background color for the text.

