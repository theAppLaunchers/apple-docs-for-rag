

- MapKit JS
- mapkit.CoordinateSpan
-  mapkit.CoordinateSpan 

Initializer

# mapkit.CoordinateSpan

Creates a new coordinate span object with the specified latitude and longitude deltas.

MapKit JS 5.0+

``` source
new mapkit.CoordinateSpan(
 number latitudeDelta,
 number longitudeDelta
);
```

## Parameters 

`latitudeDelta`  

The amount of north-to-south distance (in degrees) to display for the map region. Unlike longitudinal distances, which vary based on the latitude, one degree of latitude is always approximately 111 km (69 mi.).

`longitudeDelta`  

The amount of east-to-west distance (in degrees) to display for the map region. The number of kilometers (or miles) that a longitude range spans varies based on the latitude. For example, one degree of longitude spans a distance of approximately 111 km (69 miles mi.) at the equator, approximately 88 km (or 55mi.) at 37º north latitude (the latitude of San Francisco), and shrinks to 0 km (0 mi.) at the poles.

## Discussion

The latitude and longitude delta parameters need to be positive numbers. MapKit JS treats negative numbers as zero.

```
var span = new mapkit.CoordinateSpan(.016, .016); // The initializer requires parameters in the order of latitude delta, longitude delta.
```

