

- RealityKit
- ShapeResource
-  generateStaticMesh(positions:faceIndices:) 

Type Method

# generateStaticMesh(positions:faceIndices:)

Creates a static collision mesh from an array of vertex positions and face indices.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+visionOS 1.0+

``` source
nonisolated
static func generateStaticMesh(
    positions: [SIMD3],
    faceIndices: [UInt16]
) async throws -> ShapeResource
```

## Parameters 

`positions`  

An array of vertex positions containing discrete points on the mesh.

`faceIndices`  

An array of integers used to index into the position array. Each three indices define a polygon in the mesh.

## Discussion

The triangle mesh is pre-processed into an optimized format before being used by the physics engine. The pre-processing step can take significant time if the position counts are large. To minimize this cost, the position count should be as small as possible. The returned `ShapeResource` can only be used under the following circumstances:

- This shape can only be used with `PhysicsBodyMode.static` and not `.dynamic` or `.kinematic`.

- This shape cannot be used with `CollisionComponent.Mode.trigger`.

