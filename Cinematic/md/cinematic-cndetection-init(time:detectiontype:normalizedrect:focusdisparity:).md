

- Cinematic
- CNDetection
-  init(time:detectionType:normalizedRect:focusDisparity:) 

Initializer

# init(time:detectionType:normalizedRect:focusDisparity:)

Creates a Cinematic detection of a subject.

iOS 17.0+iPadOS 17.0+macOS 14.0+tvOS 17.0+

``` source
init(
    time: CMTime,
    detectionType: CNDetectionType,
    normalizedRect: CGRect,
    focusDisparity: Float
)
```

## Parameters 

`time`  

The presentation time of the frame that the detection occurred.

`detectionType`  

The type of object detected, such as the face, torso, cat, dog, and so on.

`normalizedRect`  

The rectangle within the image where the object occurs, normalized such that (0.0, 0.0) is the top-left and (1.0, 1.0) is the bottom-right.

`focusDisparity`  

The disparity to use in order to focus on the object.

