

- ARKit
- ARCamera
-  projectionMatrix 

Instance Property

# projectionMatrix

A transform matrix appropriate for rendering 3D content to match the image captured by the camera.

iOS 11.0+iPadOS 11.0+Mac Catalyst 13.1+

``` source
var projectionMatrix: simd_float4x4 { get }
```

## Discussion

Reading this property’s value is equivalent to calling the `projectionMatrix(withViewportSize:orientation:zNear:zFar:)` method, using the camera’s imageResolution and intrinsics properties to derive size and orientation, and passing default values of `0.001` and `1000.0` for the near and far clipping planes.

## See Also

### Applying Camera Geometry

func projectionMatrix(for: UIInterfaceOrientation, viewportSize: CGSize, zNear: CGFloat, zFar: CGFloat) -> simd_float4x4

Returns a transform matrix appropriate for rendering 3D content to match the image captured by the camera, using the specified parameters.

func viewMatrix(for: UIInterfaceOrientation) -> simd_float4x4

Returns a transform matrix for converting from world space to camera space.

func projectPoint(simd_float3, orientation: UIInterfaceOrientation, viewportSize: CGSize) -> CGPoint

Returns the projection of a point from the 3D world space detected by ARKit into the 2D space of a view rendering the scene.

func unprojectPoint(CGPoint, ontoPlane: simd_float4x4, orientation: UIInterfaceOrientation, viewportSize: CGSize) -> simd_float3?

Returns the projection of a point from the 2D space of a view rendering the scene onto a plane in the 3D world space detected by ARKit.

