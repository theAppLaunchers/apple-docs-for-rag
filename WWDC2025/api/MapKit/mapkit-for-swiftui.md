Collection

*   [MapKit](/documentation/mapkit)
*   MapKit for SwiftUI

API Collection

# MapKit for SwiftUI

MapKit for SwiftUI allows you to build map-centric views and apps across Apple platforms. You can design expressive and highly interactive Maps with minimal code by composing views, using ViewBuilders and view modifiers.

## [Overview](/documentation/MapKit/mapkit-for-swiftui#overview)

Like MapKit for AppKit and UIKit, MapKit for SwiftUI allows you to take advantage of map styles ranging from satellite imagery to rich, 3D perspective imagery to present vivid maps. Using [`MapContentBuilder`](/documentation/mapkit/mapcontentbuilder) you can configure your maps to show [`Marker`](/documentation/mapkit/marker) and [`Annotation`](/documentation/mapkit/annotation) views, or — for more specialized content — you can design your own SwiftUI views to place on the map. To add even more interactivity, MapKit for SwiftUI supports overlays to highlight areas on the map, enabling you to animate paths and directions using [`MapPolyline`](/documentation/mapkit/mappolyline), or make it easy for people to dig deeper into on the ground details with tappable points of interest. People who use your app can also explore at street level using [`LookAroundPreview`](/documentation/mapkit/lookaroundpreview) and Look Around viewer.

Note

For more information about integrating MapKit into your app using SwiftUI, see WWDC23 session 10043: [Meet MapKit for SwiftUI](https://developer.apple.com/videos/play/wwdc2023/10043/)

## [Topics](/documentation/MapKit/mapkit-for-swiftui#topics)

[

Searching, displaying, and navigating to places](/documentation/mapkit/searching-displaying-and-navigating-to-places)

Convert place information between coordinates and user-friendly place names, get cycling directions, and conveniently display formatted addresses.

### [Essentials](/documentation/MapKit/mapkit-for-swiftui#Essentials)

```swift
```swift
```swift
```swift
struct Map
```
```

A view that displays an embedded map interface.
```
```swift
```swift
```swift
struct MapStyle
```
```

A style that you can apply to a map.
```
```

### [Annotations and overlays](/documentation/MapKit/mapkit-for-swiftui#Annotations-and-overlays)

```swift
```swift
```swift
```swift
struct Annotation
```
```

A customizable annotation used to indicate a location on a map.
```
```swift
```swift
```swift
struct MapCircle
```
```

A circular overlay with a configurable radius that you center on a geographic coordinate.
```
```swift
```swift
```swift
struct MapPolygon
```
```

A closed polygon overlay.
```
```swift
```swift
```swift
struct MapPolyline
```
```

An open polygon overlay consisting of one or more connected line segments.
```
```swift
```swift
```swift
struct Marker
```
```

A balloon-shaped annotation that marks a map location.
```
```swift
```swift
```swift
struct UserAnnotation
```
```

Displays the person’s current location on the map.
```
```

### [Map controls](/documentation/MapKit/mapkit-for-swiftui#Map-controls)

```swift
```swift
```swift
```swift
struct MapCompass
```
```

A view that reflects the current orientation of the associated map.
```
```swift
```swift
```swift
struct MapLocationCompass
```
```

A view that displays a combined user location button and map compass.
```
```swift
```swift
```swift
struct MapPitchSlider
```
```

A slider control that allows a person to change the pitch of the map.
```
```swift
```swift
```swift
struct MapPitchToggle
```
```

A button that sets the pitch of the associated map.
```
```swift
```swift
```swift
struct MapScaleView
```
```

Displays a legend with distance information for the associated map.
```
```swift
```swift
```swift
struct MapUserLocationButton
```
```

A button that sets the framing of the associated map to the user location.
```
```swift
```swift
```swift
struct MapZoomStepper
```
```

Buttons a person uses to adjust the zoom level of the map.
```
```

### [Exploring at street level](/documentation/MapKit/mapkit-for-swiftui#Exploring-at-street-level)

```swift
```swift
```swift
```swift
struct LookAroundPreview
```
```

A view that provides a Look Around preview for a specific geographic location.
```
```

### [Map features](/documentation/MapKit/mapkit-for-swiftui#Map-features)

```swift
```swift
```swift
```swift
struct MapFeature
```
```

A tappable map feature.
```
```swift
```swift
```swift
struct MapSelection
```
```

A value representing a selected feature on a map.
```
```swift
```swift
```swift
protocol MapSelectable
```
```
```
```

### [Map customization](/documentation/MapKit/mapkit-for-swiftui#Map-customization)

```swift
```swift
```swift
```swift
struct MapCamera
```
```

Defines a virtual viewpoint above the map surface.
```
```swift
```swift
```swift
struct MapCameraBounds
```
```

Defines an optional boundary of an area within which the map’s center needs to remain.
```
```swift
```swift
```swift
struct MapCameraPosition
```
```

A structure that describes how to position the map’s camera within the map.
```
```swift
```swift
```swift
struct MapCameraUpdateContext
```
```

A structure that defines additional information about the map camera.
```
```swift
```swift
```swift
struct MapCameraUpdateFrequency
```
```

A structure that describes when the map camera updates.
```
```

### [Place information](/documentation/MapKit/mapkit-for-swiftui#Place-information)

```swift
```swift
```swift
```swift
struct MapItemDetailSelectionAccessoryStyle
```
```

The map item detail selection accessory style.
```
```swift
```swift
```swift
func mapItemDetailSelectionAccessory(MapItemDetailSelectionAccessoryStyle?) -> some MapContent
```
```

Specifies the selection accessory to display for the selected map item content.
```

[`static func callout(MapItemDetailSelectionAccessoryStyle.CalloutStyle) -> MapItemDetailSelectionAccessoryStyle`](/documentation/mapkit/mapitemdetailselectionaccessorystyle/callout\(_:\))

Presents the accessory as an annotation callout on the map.
```

### [Geocoding](/documentation/MapKit/mapkit-for-swiftui#Geocoding)

```swift
```swift
```swift
```swift
class MKGeocodingRequest
```
```

A class that looks up a geographic coordinate using the provided string.

Beta
```
```swift
```swift
```swift
class MKReverseGeocodingRequest
```
```

A class that looks up address strings for the provided geographic coordinates.

Beta
```
```

### [Representing places and addresses](/documentation/MapKit/mapkit-for-swiftui#Representing-places-and-addresses)

```swift
```swift
```swift
```swift
class MKMapItem
```
```

A point of interest on the map.
```
```swift
```swift
```swift
class MKAddress
```
```

A class that contains a full address, and, optionally, a short address.

Beta
```
```swift
```swift
```swift
class MKAddressRepresentations
```
```

A class that provides formatted address strings.

Beta
```

[

GeoToolbox](/documentation/GeoToolbox)

Determine place descriptor information for map coordinates.

Beta
```

### [Points of interest](/documentation/MapKit/mapkit-for-swiftui#Points-of-interest)

```swift
```swift
```swift
```swift
struct PointOfInterestCategories
```
```

A structure you use to define points of interest to include or exclude on a map.
```
```

### [Protocols](/documentation/MapKit/mapkit-for-swiftui#Protocols)

```swift
```swift
```swift
```swift
protocol DynamicMapContent
```
```

A  type of view that generates views from an underlying collection of data.
```
```swift
```swift
```swift
protocol MapContent
```
```

A protocol used to construct map content such as controls, markers, and annotations.
```
```swift
```swift
```swift
struct MapContentBuilder
```
```

A result builder that creates map content from closures you provide.
```
```swift
```swift
```swift
struct MapContentView
```
```

A view that contains content that displays on a map at a specific position, and that responds to specific interactions you specify.
```
```

### [Structures](/documentation/MapKit/mapkit-for-swiftui#Structures)

```swift
```swift
```swift
```swift
struct DefaultUserAnnotationContent
```
```

A structure that represents the view to show at the user’s location on the map.
```
```swift
```swift
```swift
struct EmptyMapContent
```
```

A map content element that doesn’t contain any content.
```
```swift
```swift
```swift
struct MapProxy
```
```

A proxy for accessing sizing information about a given map view.
```
```swift
```swift
```swift
struct MapReader
```
```

A container view that defines its contents as a function of information about the first contained map.
```
```swift
```swift
```swift
struct TupleMapContent
```
```

A view created from a Swift tuple of map content values.
```
```swift
```swift
```swift
struct MapSelectableContentView
```
```
```
```

## [See Also](/documentation/MapKit/mapkit-for-swiftui#see-also)

### [The MapKit APIs](/documentation/MapKit/mapkit-for-swiftui#The-MapKit-APIs)

[

API Reference

MapKit for AppKit and UIKit](/documentation/mapkit/mapkit-for-appkit-and-uikit)

[

Adopting unified Maps URLs](/documentation/mapkit/unified-map-urls)

Access Maps URLs and options for displaying Maps information across Apple platforms.