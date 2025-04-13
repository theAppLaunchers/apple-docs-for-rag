

- Core Location
- CLLocation
-  ellipsoidalAltitude 

Instance Property

# ellipsoidalAltitude

The altitude as a height above the World Geodetic System 1984 (WGS84) ellipsoid, measured in meters.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+watchOS 8.0+

``` source
var ellipsoidalAltitude: CLLocationDistance { get }
```

## Discussion

The ellipsoidalAltitude property represents the altitude above the WGS84 ellipsoid associated with a location. Use the ellipsoidalAltitude property when your geodetic application needs an altitude with respect to a standard reference frame. Use altitude if your application needs an altitude with respect to the approximate mean sea level.

The ellipsoidalAltitude value is valid if verticalAccuracy is greater than `0`, and invalid if verticalAccuracy is `0` or below. If verticalAccuracy is `0` or below, ellipsoidalAltitude is invalid and contains the value `0.0`.

Valid values for ellipsoidalAltitude can be positive or negative. Positive values indicate altitudes above the ellipsoid. Negative values indicate altitudes below the ellipsoid.

## See Also

### Getting the location attributes

var coordinate: CLLocationCoordinate2D

The geographical coordinate information.

var altitude: CLLocationDistance

The altitude above mean sea level associated with a location, measured in meters.

typealias CLLocationDistance

A distance in meters from an existing location.

var floor: CLFloor?

The logical floor of the building in which the user is located.

var timestamp: Date

The time at which this location was determined.

var sourceInformation: CLLocationSourceInformation?

Information about the source that provides the location.

