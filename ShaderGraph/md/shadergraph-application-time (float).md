

- ShaderGraph
- Application
-  Time (float) 

ShaderGraph Node

# Time (float)

The current time in seconds.

## Parameter Types

| Output | Type  |
|--------|-------|
| `Out`  | Float |

## Discussion

The Time node outputs a float representing the current time in seconds. When applied or connected to other nodes, this value changes constantly, allowing for dynamic materials. Below is an example of a simple node graph that causes an image texture to scroll in real time.

Adding Time to the incoming texture coordinates horizontal component causes the texture to “scroll” along the horizontal plane. Below, the resulting texture applies to a cube.

 Video with custom controls. 

Play 

## See Also

### Nodes

Up Direction

The direction of the up vector.

