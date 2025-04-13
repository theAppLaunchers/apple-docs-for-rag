

- Core Graphics
- CGColor
-  init(genericCMYKCyan:magenta:yellow:black:alpha:) 

Initializer

# init(genericCMYKCyan:magenta:yellow:black:alpha:)

Creates a color in the Generic CMYK color space.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.1+macOS 10.5+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
init(
    genericCMYKCyan cyan: CGFloat,
    magenta: CGFloat,
    yellow: CGFloat,
    black: CGFloat,
    alpha: CGFloat
)
```

## Parameters 

`cyan`  

A cyan value (`0.0` - `1.0`).

`magenta`  

A magenta value (`0.0` - `1.0`).

`yellow`  

A yellow value (`0.0` - `1.0`).

`black`  

A black value (`0.0` - `1.0`).

`alpha`  

An alpha value `(0.0 - 1.0)`.

## Return Value

A color object.

## See Also

### Creating Colors

func copy() -> CGColor?

Creates a copy of an existing color.

func copy(alpha: CGFloat) -> CGColor?

Creates a copy of an existing color, substituting a new alpha value.

init(gray: CGFloat, alpha: CGFloat)

Creates a color in the Generic gray color space.

init(genericGrayGamma2_2Gray: CGFloat, alpha: CGFloat)

Creates a color in the Generic gray color space with a gamma ramp of 2.2.

init(red: CGFloat, green: CGFloat, blue: CGFloat, alpha: CGFloat)

Creates a color in the Generic RGB color space.

init(srgbRed: CGFloat, green: CGFloat, blue: CGFloat, alpha: CGFloat)

Creates a color in the sRGB color space.

init?(colorSpace: CGColorSpace, components: UnsafePointer&lt;CGFloat>)

Creates a color using a list of intensity values (including alpha) and an associated color space.

init?(patternSpace: CGColorSpace, pattern: CGPattern, components: UnsafePointer&lt;CGFloat>)

Creates a color using a list of intensity values (including alpha), a pattern color space, and a pattern.

