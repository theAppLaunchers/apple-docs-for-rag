

- Core Location
- CLBeacon
-  accuracy 

Instance Property

# accuracy

The accuracy of the proximity value, measured in meters from the beacon.

iOS 7.0+iPadOS 7.0+Mac Catalyst 13.1+macOS 10.15+

``` source
var accuracy: CLLocationAccuracy { get }
```

## Discussion

A beacon with a smaller value for accuracy is typically nearer than a beacon with a larger accuracy value.

Use this property to differentiate between beacons with the same proximity value. Do not use it to identify a precise location for the beacon. Accuracy values may fluctuate due to RF interference.

A negative value in this property signifies that the actual accuracy could not be determined.

## See Also

### Determining the distance to the beacon

var proximity: CLProximity

The relative distance to the beacon.

enum CLProximity

Constants that reflect the relative distance to a beacon.

var rssi: Int

The received signal strength of the beacon, measured in decibels.

