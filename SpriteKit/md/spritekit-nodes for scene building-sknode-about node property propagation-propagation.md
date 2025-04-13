

- SpriteKit
- Nodes for Scene Building
- SKNode
-  About Node Property Propagation 

Article

# About Node Property Propagation

Learn which properties of a node affect its child nodes.

## Overview

Changing certain properties on a node can propogate to its decendents:

| Property | Description |
|----|----|
| xScale, yScale | The node’s coordinate system is scaled by these two factors. This property affects coordinate conversion, the node’s frame, drawing, and hit testing. Its descendants are similarly scaled. |
| zPosition | The node’s draw order. Nodes with a higher `zPosition` are rendered above nodes with a lower `zPosition`. This value propagates to its descendants such that a node’s `zPosition` is equal to that of its parent node, plus any value it holds in its own `zPosition` property. |
| zRotation | The node’s coordinate system is rotated. This property affects coordinate conversion, the node’s frame, drawing, and hit testing. Its descendants are similarly scaled. |
| alpha | If the node is rendered using a blend mode, the alpha value is multiplied into any alpha value before the blend operation takes place. The descendants are similarly affected. |
| isHidden | If a node is hidden, the node and its descendants are not rendered. |
| speed | The speed at which a node processes actions is multiplied by this value. The descendants are similarly affected. |

The net effect is that a child node is rendered based not only on its own properties but also on the properties of its ancestors.

\_\_

