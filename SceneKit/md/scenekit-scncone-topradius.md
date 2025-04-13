

- SceneKit
- SCNCone
-  topRadius 

Instance Property

# topRadius

The radius of the cone’s circular top. Animatable.

iOSiPadOSMac CatalystmacOStvOSvisionOSwatchOS

``` source
var topRadius: CGFloat { get set }
```

## Discussion

The cone is centered in its local coordinate system. For example, the upper surface of a cone whose top radius is `5.0` extends from `-5.0` to `5.0` along the x- and z-axes.

If either the top or bottom radius is zero, the geometry forms a cone that tapers to an apex point at that end. If both top and bottom radii are nonzero, the geometry forms a frustum that tapers (or expands) from a circular base to a circular top. If both top and bottom radii are zero or less, or either if the top or bottom radius is less than zero, the geometry is empty. The default top radius is `0.0`.

You can animate changes to this property’s value. See Animating SceneKit Content.

## See Also

### Adjusting a Cone’s Dimensions

var bottomRadius: CGFloat

The radius of the cone’s circular base. Animatable.

var height: CGFloat

The extent of the cylinder along its y-axis. Animatable.

