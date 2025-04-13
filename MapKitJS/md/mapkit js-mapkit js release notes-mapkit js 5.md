

- MapKit JS
- MapKit JS Release Notes
-  MapKit JS 5 

Article

# MapKit JS 5

Use the most up-to-date version of MapKit JS on your website.

## Overview

This document includes release notes for updates to MapKit JS 5. You can learn more about MapKit JS version numbers and how to automatically link to the latest available version in Loading the latest version of MapKit JS.

### 5.45.0

MapKit JS 5.45.0 introduces new APIs for overlay styling and animation and a new API for searching Points of Interest within a region, and includes bug fixes.

#### New Features

- Added the ability to draw polyline overlays dynamically with new primitives for polyline overlay animation. The start and end point of the polyline rendering can be programmatically controlled with strokeStart and strokeEnd properties.

- Introduced the mapkit.LineGradient class for specifying color gradients on polyline overlays.

- Added the ability to search Points of Interest in a specific region with the new mapkit.PointsOfInterestSearch API.

#### Updates

- Updated the addItems method to return the items passed.

### 5.44.0

MapKit JS 5.44.0 introduces new properties for Directions, increases the maximum zoom level for Standard maps, and includes a bug fix for mouse event handling.

#### New Features

- Added departureDate and arrivalDate properties to the mapkit.Directions API that enable more accurate travel time predictions based on arrival or departure date.

- Increased maximum zoom level on the Standard style map to improve visibility of indoor map details.

#### Updates

- Updated the behavior for disabled overlays so that they no longer capture `single-tap` events. For more information see Handling map events.

### 5.43.1

MapKit JS 5.43.1 includes a bug fix for setting the visible region on map construction.

#### Updates

- Ensured the specified visible region is honored on map construction. (Feedback ID: 7626496)

### 5.42.1

MapKit JS 5.42.1 includes bug fixes for rotation events and map regions.

#### Updates

- Ensured that `preventDefault()` can be used with `rotation-start`, like other map events described in Handling map events.

- Ensured that MapKit JS shows the same area if a developer uses the same mapkit.CoordinateRegion to set the viewable map area during initialization and to later change the viewable map area with setRegionAnimated. (Feedback ID: 7626496)

### 5.41.1

MapKit JS 5.41.1 includes enhancements to the mapkit.Geocoder and mapkit.Search responses, plus bug fixes for rotation events and very large maps.

#### New Features

- GeocoderResponse and SearchResponse now return individual address components like `country`, `locality`, and `postCode` in addition to the `formattedAddress` string.

#### Updates

- Fixed rotation issues occurring in unusual circumstances such as setting rotation to infinity and setting rotation multiple times during map initialization.

- Made sure that the map doesn’t encounter errors during panning when displayed fullscreen on very large displays.

### 5.40.0

MapKit JS 5.40.0 includes bug fixes for event reporting and controls.

#### Updates

- Added asynchronous reporting of failed configuration.

- Improved visibility of map controls in Chrome by decreasing their transparency in dark mode.

- Added the ability to reset the map rotation to zero by pressing the spacebar when the compass control has focus.

### 5.39.0

MapKit JS 5.39.0 includes bug fixes for tile overlays and controls.

#### Updates

- Added the ability to set `tileOverlays` in the `mapkit.Map` constructor.

- Ensured that the Apple Maps logo remains the same size whether the map is in Standard or Hybrid mode.

### 5.38.1

MapKit JS 5.38.1 includes bug fixes for annotations, annotation clustering, and controls.

#### Updates

- Show default marker annotation appearance (red balloon with a white pin glyph) when the image for an `ImageAnnotation` can’t be found.

- Ensured annotation clustering doesn’t animate if the clusters aren’t visible.

- Made sure that annotation cluster positions stay consistent when zooming.

- Made sure that the Apple logo and Legal link are always visible on the map, even if `padding` has a negative value.

### 5.36.0

MapKit JS 5.36.0 includes bug fixes.

#### Updates

- Ensured that the `distances` property can be set when creating a new map object. (Feedback ID: 7451047)

- Reworded warnings for `TileOverlay` minimum zoom level.

### 5.35.0

MapKit JS 5.35.0 includes bug fixes for Point of Interest (POI) Filtering and performance.

#### Updates

- Ensured that `map.pointOfInterestFilter.includesCategory` returns `false` when POI aren’t showing on the map.

- Improved rendering performance when the current location annotation is showing on the map.

- Improved panning and zooming performance when there are no annotations on the map.

### 5.34.2

MapKit JS 5.34.2 includes bug fixes for tile loading, annotations, and map controls.

#### Updates

- Ensured that the map tiles continue to load in cases where the developer initializes the map more than once. (Feedback ID: 7335445)

- Fixed `calloutAppearanceAnimationForAnnotation` for animations on custom callouts.

- Applied a dark style to the current location annotation callout when the map is in dark mode.

- Made sure that the map type control always shows the active map after opening the map type menu.

### 5.33.1

MapKit JS 5.33.1 includes new APIs for Point of Interest (POI) Filtering, plus bug fixes.

#### New Features

- Added new APIs that let a client apply filters to show or hide specific categories of Points of Interest (POIs) on the map, like “Parks” or “Restaurants”. These filters can also be applied to Search and Search Autocomplete results. For more information, see What’s New in MapKit and MapKit JS.

#### Updates

- Adjusted the order of focused controls while tabbing to be more intuitive.

- Made sure that custom annotation callouts apply the `overflow:scroll` style when the developer sets it.

- Ensured that the user location annotation doesn’t overlap other annotations added to the map.

- Prevented marker annotations from being inadvertently styled by CSS in the embedding page.

- Decreased the sensitivity of two-finger zooming to avoid unintentional zooms. For example, a zoom gesture should not be initiated when the user places two fingers on the trackpad.

### 5.32.2

MapKit JS 5.32.2 includes bug fixes for controls, annotations, and performance.

#### Updates

- Adjusted the position of the Legal link in relation to the user location control.

- Made sure clustered annotations don’t freeze when the user pans or zooms the map with gestures.

- Improved performance by drawing less often.

### 5.30.1

MapKit JS 5.30.1 includes an improvement to the way marker annotation titles and subtitles render, and minor bug fixes.

#### Updates

- Increased width for marker annotation titles and subtitles so that more text can fit on a single line before breaking.

- Made sure the grab hand cursor shows up when panning a map that is displayed in an HTML `iframe`.

### 5.29.0

MapKit JS 5.29.0 improves accessibility, performance, and the appearance of controls when they are mirrored for right-to-left languages.

#### Updates

- Improved the performance of importGeoJSON by ensuring that the main thread is never blocked.

- Updated controls so that when a user clicks or taps a control that has focus, it retains focus.

- Ensured controls that mirror for right-to-left languages also mirror the pressed state of the zoom buttons.

### 5.28.1

MapKit JS 5.28.1 improves keyboard navigation, fixes memory leaks, and addresses developer feedback.

#### Updates

- Improved keyboard navigation on the map type control.

- Updated so MapKit JS defaults to HTTPS for CDN connections whenever possible. (Feedback ID: 6790373)

- Fixed a memory leak created when MapKit JS called `destroy()` while the user location error panel was visible.

- Updated the list of POI Filtering categories, removing `ReligiousSite` and `Playground`. POI Filtering (introduced at WWDC 2019) becomes available in the fall of 2019.

### 5.25.0

MapKit JS 5.25.0 includes various improvements for controls, GeoJSON import, and annotation clusters.

#### Updates

- MapKit JS controls (+/- buttons, compass, Legal link, and so on) are no longer affected by CSS on the enclosing page.

- Updated the Legal link so it connects to HI-IN, IW-IL, and VI-VN localized pages when MapKit JS is running one of these languages.

- Updated spacing on the Apple Maps logo.

- Made various improvements to GeoJSON import, such as adding the ability to handle null geometries in Features, ensuring that an ItemCollection is returned even for single item imports, and improving error message reporting.

- Improved clustering behavior when member annotations are on both sides of the antimeridian.

- Ensured that annotationsInMapRect does not return cluster annotations, to match the behavior of annotations.

### 5.24.0

MapKit JS 5.24.0 includes various improvements, including changes to how the Apple Maps logo and Legal link are displayed.

#### Updates

- Improved how marker annotations animate in and out of clusters.

- Improved how annotation clusters are grouped, so that one annotation cluster never overlaps another.

- The showItems function now updates the map region in a way that encloses annotation callouts visible on selected annotations, so that any callouts showing will not be cut off the edge of the map.

- The Legal link is now always shown, for all map dimensions.

- The Apple Maps logo in the lower left corner is now displayed on maps with dimensions of 200 x 100 pixels and larger.

- The time to detect a `long-press` map event has been increased to 500 ms. See Handling map events for more information.

- Improve how cameraZoomRange and cameraBoundary behave for users in China.

### 5.23.1

MapKit JS 5.23.1 includes new APIs for region and zoom limits, an updated Apple Maps logo, and more.

#### New Features

- Added the cameraDistance property, which sets the altitude of the camera above the center of the map. A change to the map’s camera distance can be animated with setCameraDistanceAnimated.

- Added the cameraZoomRange property, which restricts zooming to a specified minimum and maximum camera distance. A change to the map’s camera zoom range can be animated with setCameraZoomRangeAnimated.

- Added the cameraBoundary property, which restricts panning to a specified coordinate region. A change to the map’s camera boundary can be animated with setCameraBoundaryAnimated.

- Enabled Directions support for users in China.

- Updated logo in the lower left corner from the Apple icon to the icon beside the word “Maps”.

#### Updates

- Fixed issue where importGeoJSON would not import a `GeometryCollection` nested within a `Feature.`

- Improved how the default marker annotation color is set depending on the map’s colorScheme. Setting a marker annotation’s color property to `null` sets a default color that matches the current colorScheme.

- Updated the Legal link on the map to open a web page, instead of displaying a menu.

### 5.22.0

The MapKit JS 5.22.0 release adds improvements to browser support.

#### New Features

- Added pinch-zoom on trackpad support for Chrome and Firefox.

#### Updates

- Improved performance of mouse wheel zoom for Firefox on Windows.

- Prevented nontouch events from firing during touch gestures in Firefox.

### 5.21.0

The MapKit JS 5.21.0 release includes a rotation gesture improvement.

#### Updates

- Fixed bug where rotating the map with gesture was not working in Chrome on Android.

### 5.20.3

The MapKit JS 5.20.3 release includes bug fixes and performance improvements.

#### Updates

- Fixed bug where `https:` was not selected for CDN URLs in some packaged and local environments. (Feedback ID: 48289622)

- Improved annotation CSS to prevent collision with styles on host implementations.

- Improved annotations to warn instead of throw an error in some selection and deselection cases.

- Improved positioning logic for Annotation glyph text.

- Improved performance of annotation image assets.

- Fixed bug in callout where glyphImage was always used instead of selectedGlyphImage where appropriate.

### 5.19.1

The MapKit JS 5.19.1 release includes minor fixes and performance improvements.

### 5.18.0

The MapKit JS 5.18.0 release includes new map interaction events and bug fixes.

#### New Features

- Added map interaction events (single-tap, double-tap, and long-press), which are dispatched by the map when the user does a single tap, a double tap, or a long press, but only when the gesture has no effect on the map (such as selecting an annotation or zooming in).

#### Updates

- Updated the behavior of setters that cause a selection state to change. For example, setting a `selected` property or adding a selected annotation cannot be done within the callback of `select` or `deselect` event listeners. Doing so will throw an error.

- Improved rotation animation when a map has padding.

- Fixed issue where a language set by a property (instead of by the MapKitInitOptions) would be reset upon initialization.

### 5.17.1

The MapKit JS 5.17.1 release improves the behavior of rotation when a map has padding.

#### Updates

- Fixed issue where rotation was reset after certain map interactions.

- Fixed compass control to correctly rotate around the center when the map has padding.

### 5.16.0

The MapKit JS 5.16.0 release includes new APIs that let developers inset the collision rectangle of annotations.

#### Updates

- Added support for insetting the collision rectangle of annotations with the padding property of Annotations.

### 5.15.0

The MapKit JS 5.15.0 release includes improvements to the display of annotation and overlay items.

#### Updates

- Improved computation of scale to better respect the padding configuration around items.

### 5.13.0

MapKit JS 5.13.0 includes new APIs that allow you to present maps in various styles and choose the kind of units in which to display distance.

#### New Features

- Added support for displaying the map in a muted style, which can be enabled by setting the mapType property to MutedStandard.

- Added support for displaying the map in dark mode, which can be enabled by setting the new colorScheme property on the Map object to Dark. The default value for colorScheme is Light.

- Added support for customizing the display of distances, as in the scale control. The new distances property on the Map object can be set to Metric or Imperial to always display metric or imperial units, respectively.

#### Updates

- Improved adaptive behavior of annotations when the map type switches.

- Fixed selection delay for annotations on a map with zoom disabled.

### 5.11.1

The MapKit JS 5.11.1 release includes bug fixes.

#### Updates

- Cluster annotations display improvements when switching to Hindi and RTL languages.

- Annotations clear from the map immediately when setting the annotations array to `[]`.

### 5.10.2

The MapKit JS 5.10.2 release includes performance improvements and bug fixes.

#### Updates

- Setting isScrollEnabled to false can disable scrolling for the enclosing web page on touch devices. (Feedback ID: 45583214)

- `navigator.geolocation.watchPosition` is `undefined`. (Feedback ID: 44311161)

- The Legal link has moved to the bottom-left of the map, next to the Apple logo.

- Improved overall performance when there are hundreds of annotations on the map.

- Improved gesture recognition to prevent accidental rotation.

- Improved VoiceOver support for the compass control.

- Fixed scenario where the compass image was requested too often.

- Fixed zooming, rotation, and panning gestures in Chrome Beta 68.

- Fixed error when map wrapped by a React component is destroyed.

### 5.7.0

MapKit JS 5.7.0 includes minor API changes, support for the new underlying map with Apple data in supported regions, annotation improvements, and more.

This update also introduces a MapKit JS Usage Dashboard to help monitor API usage against daily limits.

#### New Features

- A new property on the mapkit object named maps. Map instances are added to this array when they are initialized and removed as soon as they are destroyed.

- MapKit JS Usage Dashboard that reports the number map initializations and service calls made by your team.

#### Updates

- Added detailed building outlines and parking lots, better road network coverage, and more, in supported areas.

- mapkit.MarkerAnnotation has been updated so that instances with the same clusteringIdentifier cluster together regardless of their displayPriority value.

- When displayPriority is set, the animation for the appearance and disappearance of mapkit.MarkerAnnotation can be triggered. Now, the animation will also be triggered when an annotation is hidden by other annotations or when it reappears after a change in zoom level.

- The DirectionsResponse now includes a polyline property. The value of this property is a mapkit.PolylineOverlay, and can be added directly to a map.

#### Deprecated Features

- The path property of the DirectionsResponse is now deprecated in favor of the new polyline property.

