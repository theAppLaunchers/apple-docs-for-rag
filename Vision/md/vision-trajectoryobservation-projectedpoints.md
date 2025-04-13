

- Vision
- TrajectoryObservation
-  projectedPoints 

Instance Property

# projectedPoints

The centroids of the calculated trajectory from the detected points.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+tvOS 18.0+visionOS 2.0+

``` source
let projectedPoints: [NormalizedPoint]
```

## Discussion

The projected points define the ideal trajectory described by the parabolic equation. The equation’s coefficients and the projected points of the detected trajectory get refined over time. The system limits the maximum number of cached points to the maximum points needed to describe the trajectory together with the parabolic equation.

## See Also

### Inspecting an observation

let detectedPoints: [NormalizedPoint]

The centroid points of the detected contour along the trajectory.

let equationCoefficients: simd_float3

The coefficients of the parabolic equation.

let movingAverageRadius: CGFloat

The moving average radius of the object the request is tracking.

