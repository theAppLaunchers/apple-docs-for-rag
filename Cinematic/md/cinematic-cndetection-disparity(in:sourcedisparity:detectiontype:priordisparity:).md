

- Cinematic
- CNDetection
-  disparity(in:sourceDisparity:detectionType:priorDisparity:) 

Type Method

# disparity(in:sourceDisparity:detectionType:priorDisparity:)

Determines the disparity to use to focus on the object in the rectangle.

iOS 17.0+iPadOS 17.0+macOS 14.0+tvOS 17.0+

``` source
static func disparity(
    in normalizedRect: CGRect,
    sourceDisparity: CVPixelBuffer,
    detectionType: CNDetectionType,
    priorDisparity: Float? = nil
) -> Float
```

## Parameters 

`normalizedRect`  

The rectangle within the image where the object occurs, normalized such that (0.0, 0.0) is the top-left and (1.0, 1.0) is the bottom-right.

`sourceDisparity`  

The disparity buffer containing depth information

`detectionType`  

The type of object expected within the rectangle. Pass \`CNDetectionTypeUnknown\` if unknown.

`priorDisparity`  

The disparity of the object in the prior frame. This helps ensure the object isn’t mistaken for another that enters the same rectangle. Pass \`NAN\` if there’s no known prior, such as in the first frame in which the tracked object.

## Return Value

A float representing the disparity to use to focus on the object in the rectangle.

