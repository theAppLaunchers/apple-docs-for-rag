

- MapKit JS
- mapkit
-  Overlays 

API Collection

# Overlays

Create overlays to highlight geographic regions or paths.

## Overview

You can enhance your maps by adding *overlays,* shapes that appear on top of the map. There are three overlay shapes:

- Circle (mapkit.CircleOverlay)

- Polyline (mapkit.PolylineOverlay)

- Polygon (mapkit.PolygonOverlay)

These three objects can satisfy a wide variety of purposes, such as outlining routes, highlighting map areas, enabling users to make selections, and more.

To display an overlay, you provide geometry data that determines the overlay’s shape, and a style that determines its visual representation. For example, a circle’s center and radius define its geometry. The coordinates of a polygon’s vertices define its shape. The style specifies how to draw the overlay, including its fill color, outline color, and opacity.

Overlays are dynamic. The system automatically redraws them when their underlying geometry or style data changes. For instance, a circle’s radius can grow, or a polygon’s fill color can update dynamically. This makes overlays a powerful visualization tool. For example, circle overlays can show the spread of an infectious disease over a span of time.

Overlays belong to their own layer that lies above map tiles and below annotations. The order that you add overlays to a map is significant. When multiple overlays overlap, overlays that you add later are higher in the z-order (that is, closer to the foreground).

## Topics

### Overlays

Adding interactivity to overlays

Configure and respond to overlays to make them interactive.

mapkit.Overlay

An abstract base object that defines the methods and attributes for map overlays.

mapkit.Style

A set of observable attributes for overlays, including the color and opacity of strokes and fills, and line styles.

mapkit.CircleOverlay

A circular overlay with a configurable radius that centers on a specific geographic coordinate.

mapkit.PolylineOverlay

An overlay of connected line segments that don’t form a closed shape.

mapkit.PolygonOverlay

An overlay consisting of one or more points that forms a closed shape.

OverlayOptions

A dictionary of options that determines an overlay’s data, and indicates whether it’s visible, in an enabled state, and in a selected state.

mapkit.TileOverlay

An overlay that covers an area of the map with bitmapped tiles.

## See Also

### Annotations and overlays

Annotations

Create annotations to add indicators and additional details for specific locations on a map.

