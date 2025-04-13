

- RealityKit
-  blend(\_:\_:name:isAdditive:) 

Function

# blend(\_:\_:name:isAdditive:)

Combines the animations that result from two blend-tree nodes into a single blend-tree node.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+visionOS

``` source
func blend(
    _ x: any BlendTreeNode,
    _ y: any BlendTreeNode,
    name: String = "",
    isAdditive: Bool = false
) -> any BlendTreeNode
```

## Parameters 

`x`  

A blend-tree node whose animation combines with the second animation argument.

`y`  

A blend-tree node whose animation combines with the first animation argument.

`name`  

A unique name for the combined node.

`isAdditive`  

A Boolean value that indicates whether the animation builds on the current state of the target entity, or resets the state before running.

## Return Value

A blend-tree node that combines the given animations.

## See Also

### Blending animations

func blend(sources: [any BlendTreeNode], name: String, isAdditive: Bool) -> any BlendTreeNode

Combines the animations that result from the individual blend-tree nodes of the given array to a single blend-tree node.

