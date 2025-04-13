

- RealityKit
- PhysicallyBasedMaterial
- PhysicallyBasedMaterial.Roughness
-  PhysicallyBasedMaterial.Roughness.FloatLiteralType 

Type Alias

# PhysicallyBasedMaterial.Roughness.FloatLiteralType

A type that represents a floating-point literal.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+visionOS

``` source
typealias FloatLiteralType = Float
```

## Discussion

Valid types for `FloatLiteralType` are `Float`, `Double`, and `Float80` where available.

## See Also

### Accessing roughness data

var texture: PhysicallyBasedMaterial.Texture?

The roughness values as a UV-mapped image texture.

static let textureSemantic: TextureResource.Semantic

The intended use of the object’s texture property.

var scale: Float

The roughness value for the entire entity.

