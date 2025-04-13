

- SpriteKit
- Nodes for Scene Building
- SKSpriteNode
-  Using the Anchor Point to Move a Sprite 

Article

# Using the Anchor Point to Move a Sprite

Learn how the anchor point affects a sprite’s position.

## Overview

By default, the sprite node’s frame—and thus its texture—is centered on its position. However, you might want a different part of the texture to appear at the node’s position; for example, when the game element depicted in the texture is not centered in the texture image.

A sprite node’s anchorPoint determines which point within its frame corresponds to its position. Anchor points are specified in the unit coordinate system, shown in the following illustration. The unit coordinate system places the origin at the bottom left corner of the frame and `(1,1)` at the top right corner of the frame. A sprite’s anchor point defaults to `(0.5,0.5)`, which corresponds to the center of the frame.

Although you are moving the frame, you do this because you want the corresponding portion of the texture to be centered on the node’s position. The following figure shows two pairs of texture images. In the first, the default anchor point centers the texture on the node position. In the second, a point at the top of the image is selected instead. You can see that when the node is rotated, the texture image rotates around this point.

The following code shows how to place the anchor point on the rocket’s nose cone. Usually, you set the anchor point when the sprite node is initialized, because it corresponds to the artwork. However, you can set this property at any time. The frame is immediately updated, and the node onscreen is updated the next time the scene is rendered.

- Swift
- Obj-C

```
rocket.anchorPoint = CGPoint(x: 0.5, y: 1.0)
```

```
rocket.anchorPoint = CGPointMake(0.5,1.0);
```

## See Also

### Setting a Sprite’s Size and Position

var size: CGSize

The dimensions of the sprite, in points.

func scale(to: CGSize)

Scales the sprite node to a specified size.

var anchorPoint: CGPoint

Defines the point in the sprite that corresponds to the node’s position.

