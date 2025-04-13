

- MapKit
- MKMapCamera
-  heading 

Instance Property

# heading

The heading of the camera (in degrees) relative to true north.

iOS 7.0+iPadOS 7.0+Mac Catalyst 13.1+macOS 10.9+tvOS 9.2+visionOS 1.0+

``` source
var heading: CLLocationDirection { get set }
```

## Discussion

The value `0` means that the top edge of the map view corresponds to true north. The value `90` means the top of the map is pointing due east. The value `180` means the top of the map points due south, and so on.

## See Also

### Configuring the viewing angle

var centerCoordinate: CLLocationCoordinate2D

The map coordinate at the center of the map view.

var centerCoordinateDistance: CLLocationDistance

The distance from the center point of the map to the camera, in meters.

var pitch: CGFloat

The viewing angle of the camera, in degrees.

var altitude: CLLocationDistance

The altitude above the ground, in meters.

Deprecated

