

- PHASE
- PHASEShape
-  init(engine:mesh:materials:) 

Initializer

# init(engine:mesh:materials:)

Creates an object of a specific material that the given geometric data shapes.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 17.0+visionOS 1.0+

``` source
convenience init(
    engine: PHASEEngine,
    mesh: MDLMesh,
    materials: [PHASEMaterial]
)
```

## Parameters 

`engine`  

The object that controls this class’s associated audio output.

`mesh`  

A collection of points that connect to form a shape.

`materials`  

An array of objects that describe surface characteristics.

## Discussion

The framework assigns a material from the material array for every submesh in the mesh object. For example, PHASE infers that the first mesh is wooden if the first element of the material array is PHASEMaterialPreset.wood.

If the number of submeshes within the mesh is less than or equal to the material array count, each material indexes the corresponding element. If the number of submeshes is greater than the material array count, each material indexes the element at the element index modulo the material count.

The framework generates an error for empty material arrays or `nil` array entries.

## See Also

### Creating a Shape

init(engine: PHASEEngine, mesh: MDLMesh)

Creates an object that the given geometric data shapes.

