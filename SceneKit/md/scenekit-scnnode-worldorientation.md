

- SceneKit
- SCNNode
-  worldOrientation 

Instance Property

# worldOrientation

The node’s orientation relative to the scene’s world coordinate space.

iOS 11.0+iPadOS 11.0+Mac Catalyst 13.1+macOS 10.13+tvOS 11.0+visionOS 1.0+watchOS 4.0+

``` source
var worldOrientation: SCNQuaternion { get set }
```

## Discussion

This quaternion isolates the rotational aspect of the node’s worldTransform matrix, which in turn is the conversion of the node’s transform from local space to the scene’s world coordinate space. That is, it expresses the difference in axis and angle of rotation between the node and the scene’s rootNode.

## See Also

### Related Documentation

var simdWorldOrientation: simd_quatf

The node’s orientation relative to the scene’s world coordinate space.

### Managing Transforms in World Space (SceneKit Types)

var worldTransform: SCNMatrix4

The world transform applied to the node.

func setWorldTransform(SCNMatrix4)

Sets the world transform applied to the node.

var worldPosition: SCNVector3

The node’s position relative to the scene’s world coordinate space.

