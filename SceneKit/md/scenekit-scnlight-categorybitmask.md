

- SceneKit
- SCNLight
-  categoryBitMask 

Instance Property

# categoryBitMask

A mask that defines which categories this light belongs to.

iOSiPadOSMac Catalyst 13.1+macOS 10.10+tvOSvisionOSwatchOS

``` source
var categoryBitMask: Int { get set }
```

## Discussion

You can assign each light and each node in a scene to one or more categories, each corresponding to a bit in the bit mask. You define the mask values used in your app. When SceneKit renders a scene, it compares the categoryBitMask property of each node with that of each light using a bitwise AND operation. If the result is a nonzero value, SceneKit uses that light when rendering that node.

Use this property to make some lights in your scene apply only to certain nodes. The rendering performance cost of dynamic lighting increases with the number of lights affecting a node—you can reduce this performance cost by using category bit masks to limit the number of lights illuminating each node.

The default mask has all bits set, meaning that nodes of all categories are lit by the light.

