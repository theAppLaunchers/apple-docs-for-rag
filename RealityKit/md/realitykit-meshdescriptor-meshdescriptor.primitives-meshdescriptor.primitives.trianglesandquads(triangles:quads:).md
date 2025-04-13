

- RealityKit
- MeshDescriptor
- MeshDescriptor.Primitives
-  MeshDescriptor.Primitives.trianglesAndQuads(triangles:quads:) 

Case

# MeshDescriptor.Primitives.trianglesAndQuads(triangles:quads:)

Defines separate arrays for triangle and quad indices.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+visionOS

``` source
case trianglesAndQuads(
    triangles: [UInt32],
    quads: [UInt32]
)
```

## Discussion

The elements of the first array have three vertex indices for each triangle. The elements of the first array have four vertex indices for each quadrilateral.

For example, you can define three triangles with 9 vertex indices in the first array, and two quadralaterals with 8 vertex indices in the second array.

```
.trianglesAndQuads(
    triangles: [0, 1, 2, 7, 8, 9, 42, 43, 44],
    quads: [3, 4, 5, 6, 10, 11, 12, 13]
)
```

