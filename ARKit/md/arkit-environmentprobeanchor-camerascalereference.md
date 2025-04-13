

- ARKit
- EnvironmentProbeAnchor
-  cameraScaleReference 

Instance Property

# cameraScaleReference

The camera scale reference of this anchor.

visionOS 2.0+

``` source
var cameraScaleReference: Float { get }
```

## Discussion

Returns the camera scale reference of a pixel with rgb value \[1,1,1\] in the environment texture.

In order to have a consistent brightness between texture updates, the cameraScaleReference allows you to translate the local brightness from the current environment texture to the absolute brightness range from the camera.

## See Also

### Getting anchor information

var environmentTexture: (any MTLTexture)?

The environment texture of an anchor.

var originFromAnchorTransform: simd_float4x4

The transform from the environment probe anchor to the origin coordinate system.

