

- Model I/O
- MDLCamera
-  chromaticAberration 

Instance Property

# chromaticAberration

The amount of radial color shift around the edges of an image rendered using the camera.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+macOS 10.11+tvOS 9.0+visionOS 1.0+

``` source
var chromaticAberration: Float { get set }
```

## Discussion

Chromatic aberration occurs to some degree in all lenses. It results from a lens bringing different wavelengths of light to focus at different places on the image plane. A value of `0.0` (the default) indicates no chromatic aberration, and a value of `1.0` indicates the maximum amount. Chromatic aberration affects all locations in the image according to radial distance. Chromatic aberration also occurs in head-mounted displays, and the value here can be used as an intended amount of chromatic aberration to apply to an image.

## See Also

### Modeling a Physical Lens

var barrelDistortion: Float

The first coefficient for determining the radial distortion applied to pixels rendered using the camera.

var fisheyeDistortion: Float

The second coefficient for determining the radial distortion applied to pixels rendered using the camera.

var opticalVignetting: Float

The amount of radial light attenuation around the edges of an image rendered using the camera.

var focalLength: Float

The focal length, in millimeters, of the camera’s simulated lens.

var fStop: Float

The relative aperture ratio of the camera’s simulated lens.

var apertureBladeCount: Int

The number of blades in the camera’s simulated aperture.

func bokehKernel(withSize: vector_int2) -> MDLTexture

Creates and returns a texture, based on the camera’s aperture blade count, to be used in rendering out-of-focus highlights in a scene.

var maximumCircleOfConfusion: Float

The maximum diameter, in millimeters on the imaging plane, at which light from a point source should appear in an image rendered using the camera.

var focusDistance: Float

The distance, in meters, at which the lens is focused.

var shutterOpenInterval: TimeInterval

The duration, in seconds, for which the camera’s simulated shutter is open during each frame.

