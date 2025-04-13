

- MapKit JS
- mapkit.Map
-  tracksUserLocation 

Instance Property

# tracksUserLocation

A Boolean value that determines whether to center the map on the user’s location.

MapKit JS 5.0+

``` source
attribute boolean tracksUserLocation;
```

## Discussion

Set this property to `true` to center the map on the user location annotation. Enabling this property automatically enables showsUserLocation.

Set this property to `false` to stop centering the map on the current location.

A programmatic or user-initiated change to the map’s region that moves the user location annotation off the center automatically disables tracksUserLocation.

## See Also

### Displaying the user’s location

showsUserLocation

A Boolean value that determines whether to show the user’s location on the map.

userLocationAnnotation

An annotation that indicates the user’s location on the map.

