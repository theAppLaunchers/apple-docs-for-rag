

- Core Location
- CLLocation
-  sourceInformation 

Instance Property

# sourceInformation

Information about the source that provides the location.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+watchOS 8.0+

``` source
var sourceInformation: CLLocationSourceInformation? { get }
```

## Discussion

This property enables developers to make better-informed decisions as to whether to treat certain locations differently, or reject potentially simulated locations that they generate during testing. An app may choose to check this property and reject locations if, for example, the isSimulatedBySoftware property is `true` when the developer isn’t debugging or testing the app.

Use the sourceInformation property when knowing the true location of the device (within a tolerance for estimation error and horizontal/vertical accuracy) is critical.

## See Also

### Getting the location attributes

var coordinate: CLLocationCoordinate2D

The geographical coordinate information.

var altitude: CLLocationDistance

The altitude above mean sea level associated with a location, measured in meters.

var ellipsoidalAltitude: CLLocationDistance

The altitude as a height above the World Geodetic System 1984 (WGS84) ellipsoid, measured in meters.

typealias CLLocationDistance

A distance in meters from an existing location.

var floor: CLFloor?

The logical floor of the building in which the user is located.

var timestamp: Date

The time at which this location was determined.

