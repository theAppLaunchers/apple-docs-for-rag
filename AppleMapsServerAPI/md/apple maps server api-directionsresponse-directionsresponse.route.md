

- Apple Maps Server API
- DirectionsResponse
-  DirectionsResponse.Route 

Object

# DirectionsResponse.Route

An object that represent the components of a single route.

Apple Maps Server API 1.2+

``` source
object DirectionsResponse.Route
```

## Properties

`distanceMeters`

`integer`

Total distance that the route covers, in meters.

`durationSeconds`

`integer`

The estimated time to traverse this route in seconds. If you’ve specified a `departureDate` or `arrivalDate`, then the estimated time includes traffic conditions assuming user departs or arrives at that time. If you set neither `departureDate` or `arrivalDate`, then estimated time represents current traffic conditions assuming user departs “now” from the point of origin.

`hasTolls`

`boolean`

When `true`, this route has tolls; if `false`, this route has no tolls. If the value isn’t defined (“undefined”), the route may or may not have tolls.

`name`

`string`

The route name that you can use for display purposes.

`stepIndexes`

`[integer]`

An array of integer values that you can use to determine the number steps along this route. Each value in the array corresponds to an index into the `steps` array.

`transportType`

`string`

A string that represents the mode of transportation the service used to estimate the arrival time. Same as the input query param `transportType` or `Automobile` if the input query didn’t specify a transportation type.

Possible Values: `Automobile, Walking`

## See Also

### Steps and routes

object DirectionsResponse.Step

An object that represents a step along a route.

