

- RealityKit
- IKRig
- IKRig.Joint
-  init(name:parentID:restTransform:) 

Initializer

# init(name:parentID:restTransform:)

Creates a joint with the provided base elements.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+visionOS 2.0+

``` source
init(
    name: String,
    parentID: IKRig.Joint.ID? = nil,
    restTransform: Transform = .identity
)
```

## Parameters 

`name`  

The name of the new joint.

`parentID`  

The name of the parent joint if there is one.

`restTransform`  

The offset of this joint from its parent (local space).

