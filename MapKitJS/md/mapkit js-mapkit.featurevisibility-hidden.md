

- MapKit JS
- mapkit.FeatureVisibility
-  Hidden 

Enumeration Case

# Hidden

A constant indicating that the feature is always hidden.

MapKit JS 5.0+

``` source
const string Hidden;
```

## Discussion

Use `mapkit.FeatureVisibility.Hidden` to hide adaptive map controls, such as the compass and scale. You can show or hide controls that aren’t adaptive by setting map properties to `true` or `false`, respectively.

The following example shows how to always hide the compass, the map type, and the zoom controls:

```
// Create a map.
var map = new mapkit.Map("my-map-element-id");

// Always hide the compass. 
map.showsCompass = mapkit.FeatureVisibility.Hidden;

// Hide the map type and the zoom controls.
map.showsMapTypeControl = false;
map.showsZoomControl = false;

```

## See Also

### Feature visibility values

Adaptive

A constant indicating that feature visibility adapts to the current map state.

Visible

A constant indicating that the feature is always visible.

