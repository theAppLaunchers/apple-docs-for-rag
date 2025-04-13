

- Model I/O
- MDLCamera
-  fStop 

Instance Property

# fStop

The relative aperture ratio of the camera’s simulated lens.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+macOS 10.11+tvOS 9.0+visionOS 1.0+

``` source
var fStop: Float { get set }
```

## Discussion

Relative aperture, also called *f-stop* or *f-number*, is a measure of the amount of light permitted through a lens to an imaging surface, commonly thought of as the “speed” of the lens. The f-stop is the ratio of the lens’s focalLength to the diameter of the entrance pupil. It controls the amount of light that reaches the sensor, as well as the size of out-of-focus parts of the image.

The default relative aperture is is `5.6`, simulating an f/5.6 lens.

## See Also

### Modeling a Physical Lens

var barrelDistortion: Float

The first coefficient for determining the radial distortion applied to pixels rendered using the camera.

var fisheyeDistortion: Float

The second coefficient for determining the radial distortion applied to pixels rendered using the camera.

var opticalVignetting: Float

The amount of radial light attenuation around the edges of an image rendered using the camera.

var chromaticAberration: Float

The amount of radial color shift around the edges of an image rendered using the camera.

var focalLength: Float

The focal length, in millimeters, of the camera’s simulated lens.

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

