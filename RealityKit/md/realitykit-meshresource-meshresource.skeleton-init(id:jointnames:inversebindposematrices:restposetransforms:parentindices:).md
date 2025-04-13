

- RealityKit
- MeshResource
- MeshResource.Skeleton
-  init(id:jointNames:inverseBindPoseMatrices:restPoseTransforms:parentIndices:) 

Initializer

# init(id:jointNames:inverseBindPoseMatrices:restPoseTransforms:parentIndices:)

Creates a skeleton from arrays which define its joints. Returns `nil` if there was an issue converting the parameters to a valid skeleton.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+visionOS 1.0+

``` source
init?(
    id: String,
    jointNames: [String],
    inverseBindPoseMatrices: [simd_float4x4],
    restPoseTransforms: [Transform]? = nil,
    parentIndices: [Int?]? = nil
)
```

## Parameters 

`id`  

The unique name of this skeleton.

`jointNames`  

The names of each joint.

`inverseBindPoseMatrices`  

The matrix which, for each joint, transforms from model space (bind pose) to the local space of that joint.

`restPoseTransforms`  

The transform from each joint’s local space to its parent’s local space, used when the joint is not animated. If not specified, the rest pose is assumed to be the same as the bind pose, and is computed from the inverse bind pose matrices.

`parentIndices`  

The index of each joint’s parent, or nil if that joint has no parent. If this array is not provided, the parent of each joint is inferred from its name (e.g. a joint named `root/hips_joint` is parented to a joint named `root`).

## Discussion

Note

A parent joint needs to precede all of its child joints.

Note

All the arrays passed to this initializer need to have the same length.

