

- AVFoundation
- AVDepthData
- AVDepthData.Quality
-  AVDepthData.Quality.low 

Case

# AVDepthData.Quality.low

The depth map is a poor candidate for rendering high-quality depth effects or reconstructing a 3D scene.

iOS 11.0+iPadOS 11.0+Mac Catalyst 14.0+macOS 10.13+tvOS 11.0+visionOS 1.0+

``` source
case low
```

## Discussion

Low quality occurs when the process generating the depth map (such as inference of depth from disparity on a device with dual cameras) cannot find enough distinct key points in the input images, resulting in a large number of invalid depth values in the (pre-filtered) map.

## See Also

### Depth Quality Values

case high

The depth map is a good candidate for rendering high-quality depth effects or reconstructing a 3D scene.

