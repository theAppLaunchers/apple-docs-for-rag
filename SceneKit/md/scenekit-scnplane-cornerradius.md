

- SceneKit
- SCNPlane
-  cornerRadius 

Instance Property

# cornerRadius

The radius of curvature for the plane’s corners. Animatable.

iOSiPadOSMac Catalyst 13.1+macOS 10.9+tvOSvisionOSwatchOS

``` source
var cornerRadius: CGFloat { get set }
```

## Discussion

The minimum (and default) corner radius is `0.0`, specifying square corners. Set this property to a nonzero value to add rounded corners to the plane. Setting a corner radius of less than zero creates an empty geometry.

The maximum corner radius is half the plane’s smaller dimension. For example, if a plane’s width and height properties are both `10.0`, setting a corner radius of `5.0` gives the plane a circular shape, and increasing the corner radius beyond `5.0` has no effect. If a plane has width `10.0` and height `5.0`, the maximum corner radius is `2.5`, creating a rectangular shape with circular endcaps.

You can animate changes to this property’s value. See Animating SceneKit Content.

## See Also

### Adding Rounded Corners

var cornerSegmentCount: Int

The number of line segments used to create each rounded corner of the plane. Animatable.

