

- Core Location
- CLLocation
-  init(coordinate:altitude:horizontalAccuracy:verticalAccuracy:course:speed:timestamp:) 

Initializer

# init(coordinate:altitude:horizontalAccuracy:verticalAccuracy:course:speed:timestamp:)

Creates a location object with the specified coordinate, altitude, and course information.

iOS 4.2+iPadOS 4.2+Mac Catalyst 13.1+macOS 10.7+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
init(
    coordinate: CLLocationCoordinate2D,
    altitude: CLLocationDistance,
    horizontalAccuracy hAccuracy: CLLocationAccuracy,
    verticalAccuracy vAccuracy: CLLocationAccuracy,
    course: CLLocationDirection,
    speed: CLLocationSpeed,
    timestamp: Date
)
```

## Parameters 

`coordinate`  

A coordinate structure containing the latitude and longitude values.

`altitude`  

The altitude value for the location.

`hAccuracy`  

The radius of uncertainty for the geographical coordinate, measured in meters. Specify a negative number to indicate that the geographical coordinate is invalid.

`vAccuracy`  

The accuracy of the altitude value, measured in meters. Specify a negative number to indicate that the altitude is invalid.

`course`  

The direction of travel for the location, measured in degrees relative to due north and continuing clockwise around the compass.

`speed`  

The current speed associated with this location, measured in meters per second.

`timestamp`  

The time to associate with the location object. Typically, you specify the current time.

## Return Value

A location object initialized with the specified geographical coordinate, altitude, and course information.

## Discussion

Use this method to create location objects that aren’t necessarily based on the user’s current location.Typically, you acquire location objects from your CLLocationManager object, which returns the user’s actual location. However, you might use this method when you want to represent any location on a map. For example, you might create an object to represent the user’s intended destination.

## See Also

### Creating a location object

init(latitude: CLLocationDegrees, longitude: CLLocationDegrees)

Creates a location object with the specified latitude and longitude.

init(coordinate: CLLocationCoordinate2D, altitude: CLLocationDistance, horizontalAccuracy: CLLocationAccuracy, verticalAccuracy: CLLocationAccuracy, timestamp: Date)

Creates a location object with the specified coordinate and altitude information.

init(coordinate: CLLocationCoordinate2D, altitude: CLLocationDistance, horizontalAccuracy: CLLocationAccuracy, verticalAccuracy: CLLocationAccuracy, course: CLLocationDirection, courseAccuracy: CLLocationDirectionAccuracy, speed: CLLocationSpeed, speedAccuracy: CLLocationSpeedAccuracy, timestamp: Date)

Creates a location object with the specified coordinate, altitude, course, and accuracy information.

init(coordinate: CLLocationCoordinate2D, altitude: CLLocationDistance, horizontalAccuracy: CLLocationAccuracy, verticalAccuracy: CLLocationAccuracy, course: CLLocationDirection, courseAccuracy: CLLocationDirectionAccuracy, speed: CLLocationSpeed, speedAccuracy: CLLocationSpeedAccuracy, timestamp: Date, sourceInfo: CLLocationSourceInformation)

