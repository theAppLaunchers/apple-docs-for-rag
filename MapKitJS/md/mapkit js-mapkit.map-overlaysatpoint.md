

- MapKit JS
- mapkit.Map
-  overlaysAtPoint 

Instance Method

# overlaysAtPoint

Returns an array of overlays at a given point on the webpage.

MapKit JS 5.0+

``` source
mapkit.Overlay[] overlaysAtPoint(
 DOMPoint point
);
```

## Parameters 

`point`  

A point in the page’s coordinate system, such as `new DOMPoint(event.pageX, event.pageY)`, when handling a mouse event.

## Return Value

Returns an array of overlays. If there are no overlays at the point, the array is empty.

## Discussion

If the point is above an overlay fill or stroke, MapKit JS returns the overlay. MapKit JS returns overlays in the order they display, with the first overlay in the array closest to the background, and the last overlay closest to the foreground.

Similar to overlay selection events, this method considers the overlay’s style at the point.

Note

The point needs to be above a non-null overlay fill or stroke to return the overlay.

For example, the following cases don’t return an overlay:

- The point is on an overlay’s fill, but the fill color is `null`.

- The point is on an overlay’s stroke, but the stroke color is `null`.

- The point is on an overlay’s stroke, but the line width is `0`.

Opacity isn’t a factor and can have any value. For example, if the point is on an overlay that has an opacity of `0`, MapKit JS returns that overlay.

## See Also

### Adding and removing overlays

overlays

An array of all of the map’s overlays.

selectedOverlay

The selected overlay on the map.

addOverlay

Adds an overlay to the map.

addOverlays

Adds multiple overlays to the map.

removeOverlay

Removes an overlay from the map.

removeOverlays

Removes multiple overlays from the map.

topOverlayAtPoint

Returns the topmost overlay at a given point on the webpage.

