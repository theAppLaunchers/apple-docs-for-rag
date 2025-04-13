

- MapKit
- MKMapCamera
-  init(lookingAtCenter:fromDistance:pitch:heading:) 

Initializer

# init(lookingAtCenter:fromDistance:pitch:heading:)

Returns a new camera object using the specified distance, pitch, and heading information.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+macOS 10.11+tvOS 9.0+visionOS 1.0+

``` source
convenience init(
    lookingAtCenter centerCoordinate: CLLocationCoordinate2D,
    fromDistance distance: CLLocationDistance,
    pitch: CGFloat,
    heading: CLLocationDirection
)
```

## Parameters 

`centerCoordinate`  

The coordinate point on which the framework centers the map.

`distance`  

The line-of-sight distance from the camera to the center coordinate of the map.

`pitch`  

The viewing angle of the camera, in degrees. A value of `0` results in a camera that points straight down at the map. Angles greater than `0` result in a camera that pitches toward the horizon by the specified number of degrees.

`heading`  

The heading of the camera (in degrees) relative to true north. The value `0` means that the top edge of the map view corresponds to true north. The value `90` means the top of the map points due east. The value `180` means the top of the map points due south, and so on.

## Return Value

A new camera object that initializes with the specified information.

## Discussion

You can obtain the altitude of the camera by multiplying `distance` by the cosine of the `pitch` value.

## See Also

### Getting a camera object

convenience init(lookingAtCenter: CLLocationCoordinate2D, fromEyeCoordinate: CLLocationCoordinate2D, eyeAltitude: CLLocationDistance)

Returns a new camera object using the specified viewing angle information.

convenience init(lookingAt: MKMapItem, forViewSize: CGSize, allowPitch: Bool)

Returns a new camera object using the specified map item, view size, and pitch.

