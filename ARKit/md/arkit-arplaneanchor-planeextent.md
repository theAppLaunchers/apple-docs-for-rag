

- ARKit
- ARPlaneAnchor
-  planeExtent 

Instance Property

# planeExtent

The estimated width, length, and y-axis rotation of the detected plane.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+

``` source
var planeExtent: ARPlaneExtent { get }
```

## Discussion

When ARKit first detects a plane, the resulting ARPlaneAnchor object has a center value of `(0,0,0)`, indicating that the translation portion of the anchor’s transform value locates the plane’s center point.

As the session runs, ARKit may determine that a previously detected plane anchor is part of a larger real-world surface, increasing the planeExtent width and height values. The plane’s new boundaries may not be symmetric around its initial position, so the center point changes relative to the anchor’s unchanged transform matrix.

Similarly, as the session runs, the framework may update the plane’s y-rotation to better fit its rectangular area in the environment. In iOS 15 and earlier, the framework rotates the plane anchor according to that angle. In iOS 16, the framework doesn’t rotate the anchor automatically and its transform matrix remains unchanged. Instead, the framework exposes the angle in rotationOnYAxis that you apply to any plane extent geometry in your app.

Important

Apps that run on iOS 16 with a deployment target less than iOS 16 preserve the prior y-axis rotation behavior.

## See Also

### Dimensions

var center: simd_float3

The center point of the plane relative to its anchor position.

class ARPlaneExtent

The size and y-axis rotation of a detected plane.

var extent: simd_float3

The estimated width and length of the detected plane.

Deprecated

