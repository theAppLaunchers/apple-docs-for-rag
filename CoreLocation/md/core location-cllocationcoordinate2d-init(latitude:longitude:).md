

- Core Location
- CLLocationCoordinate2D
-  init(latitude:longitude:) 

Initializer

# init(latitude:longitude:)

Creates a location coordination object with the specified latitude and longitude values.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.0+macOS 10.6+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
init(
    latitude: CLLocationDegrees,
    longitude: CLLocationDegrees
)
```

## Parameters 

`latitude`  

The latitude of the coordinate.

`longitude`  

The longitude of the coordinate.

## See Also

### Creating a location coordinate

init()

Creates a location coordinate object.

func CLLocationCoordinate2DMake(CLLocationDegrees, CLLocationDegrees) -> CLLocationCoordinate2D

Formats a latitude and longitude value into a coordinate data structure format.

