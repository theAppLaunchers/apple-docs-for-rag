

- ARKit
- ARPlaneGeometry
-  boundaryVertices 

Instance Property

# boundaryVertices

An array of vertex positions for each point along the plane’s boundary.

iOS 11.3+iPadOS 11.3+

``` source
@nonobjc
var boundaryVertices: [simd_float3] { get }
```

## Discussion

Each `float3` value in this array represents the position of a vertex along the boundary polygon of the estimated plane. The owning plane anchor’s transform matrix defines the coordinate system for these points.

This array defines the boundary polygon of the plane. Use it for purposes that require only that polygon’s definition, such as rendering an outline of the plane’s estimated shape or testing whether a point is inside the bounded region. If, instead, you need the filled shape (for example, to render a solid 3D representation of the surface), see the vertices property.

