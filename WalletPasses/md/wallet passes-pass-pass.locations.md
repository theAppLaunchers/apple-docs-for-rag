

- Wallet Passes
- Pass
-  Pass.Locations 

Object

# Pass.Locations

An object that represents a location that the system uses to show a relevant pass.

iOS 6.0+iPadOS 6.0+watchOS 2.0+

``` source
object Pass.Locations
```

## Properties

`altitude`

`double`

The altitude, in meters, of the location.

`latitude`

`double`

 (Required) 

The latitude, in degrees, of the location.

`longitude`

`double`

 (Required) 

The longitude, in degrees, of the location.

`relevantText`

`string`

The text to display on the lock screen when the pass is relevant. For example, a description of a nearby location, such as `“Store nearby on 1st and Main”`.

## See Also

### Adding relevance

Showing a Pass on the Lock Screen

Add information to your pass so the system can display it on the Lock Screen at a relevant time and place.

object Pass.Beacons

An object that represents the identifier of a Bluetooth Low Energy beacon the system uses to show a relevant pass.

object Pass.RelevantDates

An object that represents a date interval that the system uses to show a relevant pass.

