

- Cinematic
- CNObjectTracker
-  findObject(at:sourceImage:) 

Instance Method

# findObject(at:sourceImage:)

An object that finds the bounds of an object at the given point.

iOS 17.0+iPadOS 17.0+macOS 14.0+tvOS 17.0+

``` source
func findObject(
    at point: CGPoint,
    sourceImage: CVPixelBuffer
) -> CNBoundsPrediction?
```

## Parameters 

`point`  

The point of interest.

`sourceImage`  

The image buffer containing the image.

## Return Value

A prediction, which includes bounds that can be used to start tracking, or \`nil\` if no discernible object is detected.

## Discussion

Used to convert a normalized point in an image to a rectangle used to start tracking.

