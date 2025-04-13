

- Model I/O
- MDLCamera
-  exposureCompression 

Instance Property

# exposureCompression

Two parameters that determine the brightness compression curve for colors in the camera’s image.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+macOS 10.11+tvOS 9.0+visionOS 1.0+

``` source
var exposureCompression: vector_float2 { get set }
```

## Discussion

Simulating a real-world camera requires considering the way a pixel value captured by an imaging sensor is processed for display (or how a unit of film stock is developed and projected). Part of such consideration is the exposure compression function, which scales each color component value between minimum and maximum brightness.

Color values below the x component of this vector should be left unchanged. Color values at or above the y component of this vector should be clamped to the maximum display brightness. Values in between the x and y values should be smoothly scaled using a function such as a logarithmic ramp. A renderer can then derive a final pixel color (per channel) using the following formula:

`output = pow(compressionFunction(baseValue), displayGamma)`

In this formula, `compressionFunction` implements the clamping and scaling behavior described above, `baseValue` is derived as explained for the exposure property, and `displayGamma` is the gamma value of the output display device (for example, 2.0 for the default sRGB color space on Macs and iOS devices).

## See Also

### Modeling a Physical Imaging Surface

var sensorVerticalAperture: Float

The height, in millimeters, of the camera’s simulated imaging surface.

var sensorAspect: Float

The ratio of width to height for the camera’s simulated imaging surface.

var sensorEnlargement: vector_float2

The horizontal and vertical scale factors that determine the active region of the sensor.

var sensorShift: vector_float2

The horizontal and vertical offsets, in millimeters, of the center of the camera image relative to the center of the simulated lens.

var flash: vector_float3

Red, green, and blue factors to be used in brightening darker areas of the camera’s image.

var exposure: vector_float3

Red, green, and blue factors that scale each color channel in the camera’s image.

