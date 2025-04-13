

- ARKit
- ARSession
-  setWorldOrigin(relativeTransform:) 

Instance Method

# setWorldOrigin(relativeTransform:)

Changes the basis for the AR world coordinate space using the specified transform.

iOS 11.3+iPadOS 11.3+Mac Catalyst 13.1+

``` source
func setWorldOrigin(relativeTransform: simd_float4x4)
```

## Parameters 

`relativeTransform`  

A transform matrix encoding a translation and orientation relative to the session’s current world coordinate space.

## Discussion

ARKit defines a world coordinate space for you to use to place virtual content and locate detected objects in an AR experience. By default, this space is based on the initial position and orientation of the device when the session begins. However, after a session begins and has detected useful reference points (such as a plane or image), you may find it helpful to redefine the world coordinate system based on those reference points.

