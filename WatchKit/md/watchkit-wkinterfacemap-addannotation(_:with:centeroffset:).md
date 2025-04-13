

- WatchKit
- WKInterfaceMap
-  addAnnotation(\_:with:centerOffset:) 

Instance Method

# addAnnotation(\_:with:centerOffset:)

Displays the specified image on top of the map.

watchOS 2.0+

``` source
func addAnnotation(
    _ location: CLLocationCoordinate2D,
    with image: UIImage?,
    centerOffset offset: CGPoint
)
```

## Parameters 

`location`  

The location at which to display the image.

`image`  

The image to display at the specified location. If the value of this parameter is `nil`, the map adds a red pin at the specified location.

`offset`  

The offset (in points) at which to place the center of the image. Normally, the center point of an annotation image is placed at the specified location on the map. Use this parameter to reposition the image relative to that point. Positive offset values move the annotation image down and to the right, while negative values move it up and to the left.

## Discussion

This method adds an image to the map at the specified geographic location. The image is positioned just above the actual coordinate and centered on the coordinate horizontally.

## See Also

### Managing Map Annotations

func addAnnotation(CLLocationCoordinate2D, withImageNamed: String?, centerOffset: CGPoint)

Displays an image from the WatchKit app’s bundle on top of the map.

func addAnnotation(CLLocationCoordinate2D, with: WKInterfaceMapPinColor)

Adds a pin to the map at the specified location.

enum WKInterfaceMapPinColor

Constants for map pin colors.

func removeAllAnnotations()

Removes all annotations from the map.

