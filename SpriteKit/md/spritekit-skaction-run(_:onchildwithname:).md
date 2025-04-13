

- SpriteKit
- SKAction
-  run(\_:onChildWithName:) 

Type Method

# run(\_:onChildWithName:)

Creates an action that runs an action on a named child object.

iOSiPadOSMac CatalystmacOStvOSvisionOSwatchOS

``` source
class func run(
    _ action: SKAction,
    onChildWithName name: String
) -> SKAction
```

## Parameters 

`action`  

The action to execute.

`name`  

The name of a child object. See the name property on the SKNode object.

## Return Value

A new action object.

## Discussion

Because this action references child nodes by name, it is especially handy for nodes that the scene subclass (or scene delegate) does not maintain a reference to, for example, child nodes that are defined in an `.sks` file.

This action has an instantaneous duration, although the action executed on the child may have a duration of its own. When the action executes, it looks up an appropriate child node and calls its run(_:) method, passing in the action to execute.

This action is reversible; it tells the child to execute the reverse of the action specified by the `action` parameter.

