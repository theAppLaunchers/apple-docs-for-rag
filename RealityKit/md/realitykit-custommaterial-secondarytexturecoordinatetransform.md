

- RealityKit
- CustomMaterial
-  secondaryTextureCoordinateTransform 

Instance Property

# secondaryTextureCoordinateTransform

A two-dimensional transformation RealityKit applies to the entity’s secondary texture coordinates.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+

``` source
var secondaryTextureCoordinateTransform: CustomMaterial.TextureCoordinateTransform { get set }
```

## Discussion

An entity’s UV texture coordinates define how RealityKit maps image textures onto an entity. Use this property to transform the secondary texture coordinates and change the way this material maps textures onto an entity. If an entity has multiple materials assigned to it, the transformation doesn’t affect how the other materials map their textures.

For example, you might change the scale of the UV coordinates to apply a tiled, repeating pattern to the surface of your entity, or continuously rotate or translate the texture coordinates to animate materials and create special effects, such as fire or flowing liquids.

The following example demonstrates how to set a material’s UV transformation:

```
let rotationRadians = Float(45.0) * .pi / 180 // 45 degrees converted to radians.

secondaryTextureCoordinateTransform = .init(
    offset: [0.5, 0.5], scale: [0.5, 0.5],
    rotation: rotationRadians
)
```

The material’s shader function doesn’t have to do anything to apply the transformation. When the shader calls `params.geometry().uv1()`, RealityKit already transforms the returned coordinates.

## See Also

### Modifying texture coordinates

var textureCoordinateTransform: CustomMaterial.TextureCoordinateTransform

A two-dimensional transformation RealityKit applies to the entity’s primary texture coordinates.

