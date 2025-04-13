

- RealityKit
- ModelEntity
-  init(mesh:materials:collisionShape:mass:) 

Initializer

# init(mesh:materials:collisionShape:mass:)

Creates a model entity with a particular mesh, set of materials, collision shape, and mass.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+visionOS

``` source
@MainActor @preconcurrency
init(
    mesh: MeshResource,
    materials: [any Material] = [],
    collisionShape: ShapeResource,
    mass: Float
)
```

## Parameters 

`mesh`  

A mesh that defines the geometry of the model.

`materials`  

Material resources that define the appearance of the model.

`collisionShape`  

A collection of shape resources that define a composite collision shape.

`mass`  

The mass of the model in kilograms.

## See Also

### Creating a model

init()

Creates a model entity.

init(mesh: MeshResource, materials: [any Material])

Creates a model entity with a particular mesh and set of materials.

init(mesh: MeshResource, materials: [any Material], collisionShapes: [ShapeResource], mass: Float)

Creates a model entity with a particular mesh, set of materials, a composite collision shape, and mass.

