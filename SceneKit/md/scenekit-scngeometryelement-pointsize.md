

- SceneKit
- SCNGeometryElement
-  pointSize 

Instance Property

# pointSize

The width of each point in the geometry element, as measured in the geometry’s local 3D coordinate space.

iOS 11.0+iPadOS 11.0+Mac Catalyst 13.1+macOS 10.13+tvOS 11.0+visionOS 1.0+watchOS 4.0+

``` source
var pointSize: CGFloat { get set }
```

## Discussion

Some visual effects call for rendering a geometry as a collection of individual points—that is, a point cloud, not a solid surface or wireframe mesh. When you use this option, SceneKit can render each point as a small 2D surface that always faces the camera. By applying a texture or custom shader to that surface, you can efficiently render many small objects at once.

To render a geometry element as a point cloud, you must set three properties: pointSize, minimumPointScreenSpaceRadius, and maximumPointScreenSpaceRadius. Use pointSize to determine how large each point appears in world space, so that points farther away appear as smaller 2D surfaces. Use the minimum and maximum radius properties to ensure that the on-screen rendering of each point fits within a certain range of pixel sizes.

## See Also

### Rendering Point Clouds

var minimumPointScreenSpaceRadius: CGFloat

The smallest radius, measured in screen points, at which to render any point in the geometry element.

var maximumPointScreenSpaceRadius: CGFloat

The largest radius, measured in screen points, at which to render any point in the geometry element.

