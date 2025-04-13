

- SpriteKit
- SKSpriteNode
-  normalTexture 

Instance Property

# normalTexture

A texture that specifies the normal map for the sprite.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.1+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 1.0+

**watchOS**

``` source
var normalTexture: SKTexture? { get set }
```

**iOS, iPadOS, Mac Catalyst, macOS, tvOS, visionOS**

``` source
@MainActor
var normalTexture: SKTexture? { get set }
```

## Discussion

A normal map texture is used when a sprite is lit, giving it a more realistic look with shadows and specular highlights. The texture must be a normal map texture.

## See Also

### Lighting a Sprite

Lighting a Sprite with Light Nodes

Add lighting and shadows to your scene with light nodes.

var lightingBitMask: UInt32

A mask that defines how this sprite is lit by light nodes in the scene.

var shadowedBitMask: UInt32

A mask that defines which lights add shadows to the sprite.

var shadowCastBitMask: UInt32

A mask that defines which lights are occluded by this sprite.

