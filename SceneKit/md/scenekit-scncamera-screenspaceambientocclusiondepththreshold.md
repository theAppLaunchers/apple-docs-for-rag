

- SceneKit
- SCNCamera
-  screenSpaceAmbientOcclusionDepthThreshold 

Instance Property

# screenSpaceAmbientOcclusionDepthThreshold

The maximum depth difference, in units of scene space, at which to apply ambient occlusion effects.

iOS 11.0+iPadOS 11.0+Mac Catalyst 13.1+macOS 10.13+tvOS 11.0+visionOS 1.0+watchOS 4.0+

``` source
var screenSpaceAmbientOcclusionDepthThreshold: CGFloat { get set }
```

## Discussion

Ambient occlusion is an effect that improves material shading by calculating the amounts of ambient light that reach various parts of a surface, creating shadows on parts of a geometry where incoming light is obscured by other parts of the geometry. (You can provide pre-rendered ambient occlusion effects for a material using its ambientOcclusion property.) *Screen-space ambient occlusion* (SSAO) provides a real-time approximation of this effect for the entire scene viewed through the camera.

This screenSpaceAmbientOcclusionDepthThreshold property controls the effect of relative distance from the camera on SSAO effects. Higher values create more shadowing effects between foreground and background elements of the scene, but this can result in unrealistic dark halos around foreground elements that are far from the background. Lower values avoid dark halo effects, but create less visual separation between scene elements at different distances from the camera. The default value is 0.2 units.

## See Also

### Adding Screen-Space Ambient Occlusion

var screenSpaceAmbientOcclusionIntensity: CGFloat

The intensity of the screen-space ambient occlusion effect applied in camera rendering.

var screenSpaceAmbientOcclusionRadius: CGFloat

The distance, in units of scene space, at which ambient occlusion takes effect.

var screenSpaceAmbientOcclusionBias: CGFloat

An offset for modulating ambient occlusion effects.

var screenSpaceAmbientOcclusionNormalThreshold: CGFloat

The magnitude of the blur effect applied to create ambient occlusion shadows.

