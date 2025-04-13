

- MapKit JS
- mapkit
-  Annotations 

API Collection

# Annotations

Create annotations to add indicators and additional details for specific locations on a map.

## Overview

Annotations work differently in MapKit JS and native MapKit. In native MapKit, there are annotation objects and annotation views. You decide which annotation view to use for a particular annotation by implementing mapView(_:viewFor:) in the map’s delegate. In MapKit JS, there’s only the annotation, which is both model and view. You can still customize the look of annotations, but MapKit JS requires that you create annotation views explicitly rather than through a delegate.

MapKit JS shows single-point annotations on a map. The framework accomplishes this by creating a mapkit.Annotation object and adding it to a map. The framework provides three built-in objects for your convenience:

- mapkit.Annotation, which allows you to position a live DOM element on the map.

- mapkit.ImageAnnotation, which allows you to customize the annotation with your own imagery.

- mapkit.MarkerAnnotation, which places a defined *Apple look-and-feel* balloon marker on the map with a `title`, `subtitle`, and custom glyph text/image.

- mapkit.PlaceAnnotation, which places an annotation for a particular place on a map.

- mapkit.MapFeatureAnnotation, which places an image for a particular feature on a map.

A callout is a standard or custom element that can give more information about an annotation. A standard callout displays the annotation’s title and subtitle, if you provide them. A callout appears when the user selects an annotation interactively (by clicking or tapping), or programmatically when you set the annotation’s selected property to `true`. A callout goes away when the user deselects an annotation interactively either by tapping or clicking the map or by selecting another item on the map, or when you deselect it programmatically.

**Annotation events**

| Event | Summary |
|----|----|
| `select` | MapKit JS sets the annotation’s selected property to `true`. |
| `deselect` | MapKit JS sets the annotation’s selected property to `false`. |
| `drag-start` | The user initiates a drag for an annotation. A long press or click without movement isn’t a drag. |
| `dragging` | The user is dragging an annotation. This event has an extra coordinate property for the coordinate of the annotation at the time the event occurs. Note: This is different from the annotation’s own coordinate property because that property doesn’t update until the user drops the annotation. |
| `drag-end` | The user ends a drag for an annotation. |

## Topics

### Annotations

Clustering annotations

Combine multiple annotations into a single clustered annotation.

mapkit.Annotation

The base annotation object for creating custom annotations.

AnnotationCalloutDelegate

Methods for customizing the behavior and appearance of an annotation callout.

mapkit.PlaceAnnotation

An annotation for a place.

mapkit.MapFeatureAnnotation

An object that represents a map feature that the user selects.

mapkit.Annotation.CollisionMode

Constants that indicate whether an annotation collides and how to interpret the collision-frame rectangle of an annotation view.

mapkit.Annotation.DisplayPriority

Constant values that provide a hint the map uses to prioritize displaying annotations.

### Image annotations

mapkit.ImageAnnotation

A customized annotation with image resources that you provide.

### Marker annotations

mapkit.MarkerAnnotation

An annotation that displays a balloon-shaped marker at the designated location.

## See Also

### Annotations and overlays

Overlays

Create overlays to highlight geographic regions or paths.

