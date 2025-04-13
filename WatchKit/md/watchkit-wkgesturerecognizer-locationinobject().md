

- WatchKit
- WKGestureRecognizer
-  locationInObject() 

Instance Method

# locationInObject()

Returns the point computed as the current position of the touch event.

watchOS 3.0+

``` source
func locationInObject() -> CGPoint
```

## Return Value

A point in the local coordinate system of the associated interface object.

## Discussion

If multiple touches were detected, this method returns the location of only the first one.

## See Also

### Getting the Touch Information

func objectBounds() -> CGRect

Returns the dimensions of the interface object (measured in points) associated with the gesture recognizer.

