

- SceneKit
- SCNCamera
-  minimumExposure 

Instance Property

# minimumExposure

The minimum exposure value to use in tone mapping.

iOS 10.0+iPadOS 10.0+Mac Catalyst 13.1+macOS 10.12+tvOS 10.0+visionOS 1.0+watchOS 3.0+

``` source
var minimumExposure: CGFloat { get set }
```

## Discussion

When using a High Dynamic Range (HDR) camera, SceneKit applies a process called *tone mapping* to translate the wide range of luminance values in the visible scene to the narrower range of brightness values that can be shown on a display. SceneKit determines a tone mapping curve from the minimumExposure, maximumExposure, exposureOffset, and whitePoint properties, along with a measure of scene luminance.

Exposure values are exponential: a value of `1.0` doubles brightness, a value of `2.0` quadruples brightness, a value of `-1.0` halves brightness, and so on. The default value is `-15.0`. Increasing the value causes darker portions of the scene to become under-exposed (uniformly black, losing definition). Decreasing the value adds more dynamic range for darker portions of the scene; however, a greater breadth of difference between the minimum and maximum exposures decreases contrast.

This property has no effect if the wantsHDR value is false.

## See Also

### Adding High Dynamic Range Effects

var wantsHDR: Bool

A Boolean value that determines whether SceneKit applies High Dynamic Range (HDR) postprocessing effects to a scene.

var exposureOffset: CGFloat

A logarithmic bias that adjusts the results of SceneKit’s tone mapping operation, brightening or darkening the visible scene.

var averageGray: CGFloat

The luminance level to use as the midpoint of a tone mapping curve.

var whitePoint: CGFloat

The luminance level to use as the upper end of a tone mapping curve.

var maximumExposure: CGFloat

The minimum exposure value to use in tone mapping.

