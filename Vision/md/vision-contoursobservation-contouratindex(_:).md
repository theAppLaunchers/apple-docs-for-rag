

- Vision
- ContoursObservation
-  contourAtIndex(\_:) 

Instance Method

# contourAtIndex(\_:)

Retrieves the contour object at the specified index, irrespective of hierarchy.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+tvOS 18.0+visionOS 2.0+

``` source
func contourAtIndex(_ index: Int) -> ContoursObservation.Contour?
```

## Parameters 

`index`  

The index of the contour to retrieve. Valid values are in the range of `0` to `contourCount - 1`.

## Return Value

The contour object at the specified index, or `nil` if the index is invalid.

## See Also

### Getting the contours

struct Contour

An object that represents a detected contour in an image.

func countourAtIndexPath(IndexPath) -> ContoursObservation.Contour?

Retrieves the contour object at the specified index, irrespective of hierarchy.

