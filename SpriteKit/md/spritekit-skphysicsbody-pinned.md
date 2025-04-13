

- SpriteKit
- SKPhysicsBody
-  pinned 

Instance Property

# pinned

A Boolean value that indicates whether the physics body’s node is pinned to its parent node.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.1+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 1.0+

``` source
var pinned: Bool { get set }
```

## Mentioned in 

Pinning and Rotating Physics Bodies

Getting Started with Physics

## Discussion

The default value is false. If true, the node’s position is fixed relative to its parent. The node’s position cannot be changed by actions or physics forces. The node can freely rotate around its position in response to collisions or other forces. If the parent node has a physics body, the two physics bodies are treated as if they are connected with a pin joint.

## See Also

### Pinning a Physics Body to a Node’s Parent

Pinning and Rotating Physics Bodies

Pin a node so it’s free to rotate about a certain point on its parent node.

