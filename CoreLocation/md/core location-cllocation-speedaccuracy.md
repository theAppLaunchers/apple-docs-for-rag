

- Core Location
- CLLocation
-  speedAccuracy 

Instance Property

# speedAccuracy

The accuracy of the speed value, measured in meters per second.

iOS 10.0+iPadOS 10.0+Mac Catalyst 13.1+macOS 10.15+tvOS 10.0+visionOS 1.0+watchOS 3.0+

``` source
var speedAccuracy: CLLocationSpeedAccuracy { get }
```

## Discussion

When this property contains `0` or a positive number, the value in the speed property is plus or minus the specified number of meters per second. When this property contains a negative number, the value in the speed property is invalid.

## See Also

### Getting speed and course information

var speed: CLLocationSpeed

The instantaneous speed of the device, measured in meters per second.

var course: CLLocationDirection

The direction in which the device is traveling, measured in degrees and relative to due north.

var courseAccuracy: CLLocationDirectionAccuracy

The accuracy of the course value, measured in degrees.

typealias CLLocationSpeed

The velocity (measured in meters per second) at which the device is moving.

typealias CLLocationDirection

An azimuth that is measured in degrees relative to true north.

typealias CLLocationSpeedAccuracy

The accuracy of a speed.

typealias CLLocationDirectionAccuracy

The accuracy of a compass heading.

