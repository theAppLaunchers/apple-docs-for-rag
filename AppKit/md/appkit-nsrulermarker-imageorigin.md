

- AppKit
- NSRulerMarker
-  imageOrigin 

Instance Property

# imageOrigin

The point in the receiver’s image that is positioned at the receiver’s location on the ruler view.

macOS

``` source
var imageOrigin: NSPoint { get set }
```

## Discussion

For a horizontal ruler, the x coordinate of the image origin is aligned with the location of the marker, and the y coordinate lies on the baseline of the ruler. For vertical rulers, the y coordinate of the image origin is the location, and the x coordinate lies on the baseline.

## See Also

### Related Documentation

var markerLocation: CGFloat

The location of the receiver in the coordinate system of the ruler view’s client view.

### Setting the image

var image: NSImage

The receiver’s image.

var imageRectInRuler: NSRect

The rectangle occupied by the receiver’s image.

var thicknessRequiredInRuler: CGFloat

The amount of the receiver’s image that’s displayed above or to the left of the ruler view’s baseline.

