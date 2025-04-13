

- Vision
- VNHumanBodyPose3DObservation
-  pointInImage(\_:) 

Instance Method

# pointInImage(\_:)

Returns a 2D point for the joint name you specify, relative to the input image.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+tvOS 17.0+visionOS 1.0+

``` source
func pointInImage(_ jointName: VNHumanBodyPose3DObservation.JointName) throws -> VNPoint
```

## Parameters 

`jointName`  

The name of the human body joint.

## Return Value

A projection of the 3D position onto the original 2D image in normalized, lower left origin coordinates.

## Mentioned in 

Identifying 3D human body poses in images

