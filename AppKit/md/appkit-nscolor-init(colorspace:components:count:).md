

- AppKit
- NSColor
-  init(colorSpace:components:count:) 

Initializer

# init(colorSpace:components:count:)

Creates a color object from the specified components of the given color space.

macOS

``` source
init(
    colorSpace space: NSColorSpace,
    components: UnsafePointer,
    count numberOfComponents: Int
)
```

## Parameters 

`space`  

An `NSColorSpace` object representing a color space. The colorspace should be component-based. The method raises if this is `nil` or a color space that cannot be used with `NSColor` objects.

`components`  

An array of the components in the specified color space to use to create the `NSColor` object. The order of these components is determined by the color-space profile, with the alpha component always last. (If you want the created color to be opaque, specify 1.0 for the alpha component.)

`numberOfComponents`  

The number of components in the `components` array. This should match the number dictated by the specified color space plus one for alpha. This method raises an exception if they do not match.

## Return Value

The color object.

## See Also

### Related Documentation

func usingColorSpace(NSColorSpace) -> NSColor?

Creates a new color object representing the color of the current color object in the specified color space.

