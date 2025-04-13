

- SceneKit
- SCNFloor
-  reflectionResolutionScaleFactor 

Instance Property

# reflectionResolutionScaleFactor

The resolution scale factor of the offscreen buffer that SceneKit uses to render reflections.

iOSiPadOSMac Catalyst 13.1+macOS 10.10+tvOSvisionOSwatchOS

``` source
var reflectionResolutionScaleFactor: CGFloat { get set }
```

## Discussion

SceneKit creates a reflection effect by rendering the scene twice. First, it renders the scene into an offscreen buffer, using a point of view whose position is the reflection of the camera’s position. Next, it renders the scene from the camera’s point of view, using the offscreen buffer as a texture map for the floor’s surface. Rendering the scene twice incurs a performance cost. Reducing the resolution of the offscreen buffer reduces this cost but causes the reflected image to appear blurry.

The default scale factor is `1.0` in macOS and `0.5` in iOS.

## See Also

### Adding Reflections to a Floor

var reflectivity: CGFloat

The intensity of the scene’s reflection on the floor. Animatable.

var reflectionFalloffEnd: CGFloat

The distance from the floor at which scene contents are no longer reflected. Animatable.

var reflectionFalloffStart: CGFloat

The distance from the floor at which scene contents are reflected at full intensity. Animatable.

var reflectionCategoryBitMask: Int

A mask that defines which categories of other objects show reflections on the floor.

