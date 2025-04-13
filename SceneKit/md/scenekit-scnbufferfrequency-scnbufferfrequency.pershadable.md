

- SceneKit
- SCNBufferFrequency
-  SCNBufferFrequency.perShadable 

Case

# SCNBufferFrequency.perShadable

Execute the binding handler once for each frame, for each node, for each material or geometry to be rendered using the shader.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+macOS 10.11+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
case perShadable
```

## Discussion

Use this option when the contents of the buffer should be specific to each geometry or material whose program property is set to this shader. For example, a material-specific buffer might contain information to be used in animating a texture.

## See Also

### Constants

case perFrame

Execute the binding handler once for each frame to be rendered using the shader.

case perNode

Execute the binding handler once for each frame, for each node to be rendered using the shader.

