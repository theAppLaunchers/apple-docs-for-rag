

- AppKit
- NSShadow
-  shadowOffset 

Instance Property

# shadowOffset

The shadow’s relative position, which you specify with horizontal and vertical offset values.

macOS 10.0+

``` source
var shadowOffset: NSSize { get set }
```

## Discussion

This property contains the horizontal and vertical offset values that you specify using the `width` and `height` fields of the `CGSize` or `NSSize` data type. These offsets use the default user coordinate space and are not affected by custom transformations. Positive offset values extend down and to the right from the user’s perspective.

Note

In macOS 10.15 and earlier, if you add a shadow to a layer that has a different graphics context, then positive offset values might extend up and to the right from the user’s perspective, instead of down and to the right as usual.

## See Also

### Managing a shadow

var shadowBlurRadius: CGFloat

The blur radius of the shadow.

var shadowColor: NSColor?

The color of the shadow.

