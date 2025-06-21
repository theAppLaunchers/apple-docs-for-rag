*   [MapKit JS](/documentation/mapkitjs)
*   mapkit.LookAroundPreview

Class

# mapkit.LookAroundPreview

A class that renders a preview of a LookAround view.

MapKit JS 5.79+

```swift
```swift
```swift
```swift
```swift
```swift
```

```
interface mapkit.LookAroundPreview
```

```
```
```
```
```
```
```

## [Mentioned in](/documentation/MapKitJS/mapkit.LookAroundPreview#mentions)

[

Loading the latest version of MapKit JS](/documentation/mapkitjs/loading-the-latest-version-of-mapkit-js)

[

MapKit JS 5](/documentation/mapkitjs/mapkit-js-5)

## [Discussion](/documentation/MapKitJS/mapkit.LookAroundPreview#Discussion)

Note

The full bundle of MapKit JS doesn’t implement this class.

Use a `mapkit.LookAroundPreview` to create preview imagery for a specific geographic location on the map.

Note

Not all places support Look Around.

The following example contains the two elements needed to display a Look Around View on a web page:

![A screenshot showing a map view with a marker showing New York Public Library in New York, NY, and a smaller Look Around preview framing the library on the top left.](https://docs-assets.developer.apple.com/published/e7f9457ee4a834f156cf05cfd1e69252/LookAroundPreview-cl-01%402x.png)

The HTML code below implements a web page that renders a `container` which has both a map and a Look Around preview.

```

```
<script
  src="https://cdn.apple-mapkit.com/mk/5.x.x/mapkit.core.js"
  crossorigin async
  data-callback="initMapKit"
  data-token="YOUR TOKEN HERE"
  data-libraries="map,annotations,look-around,services"></script>
<style>
#map {
  width: 100%;
  height: 100%;
}
#container {
  position: absolute;
  top: 20px;
  left: 20px;
  border-radius: 20px;
  overflow: hidden;
  width: 200px;
  height: 150px;
}
</style>
<main>
  <div id="map"></div>
  <div id="container"></div>
</main>
```

```

The JavaScript listing below implements a MapKitJS map object that the web page displays inside the `<div id="map">` element of the page, with a Look Around preview displays inside the `<div id="container">` element. The code centers the map on the area near the New York Public Library in New York City using a PlaceID. The Look Around preview on the map shows a view of The New York Public Library building. For more information on obtaining a PlaceID for a specific location. For more information on Place IDs, see [Identifying unique locations with Place IDs](https://developer.apple.com/maps/place-id-lookup/).

```

```
async function initializeMapKitJS() {
  if (!window.mapkit || window.mapkit.loadedLibraries.length === 0) {
    await new Promise(res => window.initMapKit = res)
    delete window.initMapKit
  }
}
(async () => {
  await initializeMapKitJS();
  // Look Around view code
  const placeLookup = new mapkit.PlaceLookup();
  const place = await new Promise(
      resolve => placeLookup.getPlace(
        // The New York Public Library, 42nd St & 5th Ave,New York, NY
        "I88F02FEA4499C61D",
        (error, result) => resolve(result)
      )
  );
  const lookAround = new mapkit.LookAroundPreview(
      document.getElementById("container"),
      place
  );
  const map = new mapkit.Map("map", {
    center: place.coordinate,
    cameraDistance: 7000,
    showsPointsOfInterest: false,
    annotations: [
      new mapkit.PlaceAnnotation(place, {
        selected: true
      })
    ]
  });
})()
```

```

## [Handling Look Around loading states](/documentation/MapKitJS/mapkit.LookAroundPreview#Handling-Look-Around-loading-states)

LookAroundPreview object dispatches the following events:

*   `load`: The view is loaded.
    
*   `error`: The view has encountered an error, for example, in an unsupported browser, or a location with no look around imagery.
    
*   `readystatechange`: [`readyState`](/documentation/mapkitjs/mapkit.lookaroundpreview/readystate) has changed.
    
*   `open-dialog`: The view is about to expand.
    
*   `leave-dialog`: The view is about to contract.
    

## [Topics](/documentation/MapKitJS/mapkit.LookAroundPreview#topics)

### [Creating a Look Around preview](/documentation/MapKitJS/mapkit.LookAroundPreview#Creating-a-Look-Around-preview)

[`mapkit.LookAroundPreview`](/documentation/mapkitjs/mapkit.lookaroundpreview/mapkit.lookaroundpreview)

Creates a Look Around preview you embed on a webpage and initializes it with the constructor options you choose.

### [Controlling the interactions with a Look Around view](/documentation/MapKitJS/mapkit.LookAroundPreview#Controlling-the-interactions-with-a-Look-Around-view)

[`isNavigationEnabled`](/documentation/mapkitjs/mapkit.lookaroundpreview/isnavigationenabled)

A Boolean value that indicates whether someone can navigate inside the Look Around preview.

[`isScrollEnabled`](/documentation/mapkitjs/mapkit.lookaroundpreview/isscrollenabled)

A Boolean value that indicates whether someone can scroll the Look Around preview.

[`isZoomEnabled`](/documentation/mapkitjs/mapkit.lookaroundpreview/iszoomenabled)

A Boolean value that indicates whether someone can zoom the Look Around preview.

### [Controlling additional information the Look Around view displays](/documentation/MapKitJS/mapkit.LookAroundPreview#Controlling-additional-information-the-Look-Around-view-displays)

[`showsPointsOfInterest`](/documentation/mapkitjs/mapkit.lookaroundpreview/showspointsofinterest)

A Boolean value that indicates whether the Look Around preview shows points of interest (POIs).

[`showsRoadLabels`](/documentation/mapkitjs/mapkit.lookaroundpreview/showsroadlabels)

A Boolean value that indicates whether the Look Around preview shows road labels.

### [Positioning a badge](/documentation/MapKitJS/mapkit.LookAroundPreview#Positioning-a-badge)

[`badgePosition`](/documentation/mapkitjs/mapkit.lookaroundpreview/badgeposition)

A value you set to specify the position of a badge on the Look Around preview.

[`mapkit.LookAround.BadgePositions`](/documentation/mapkitjs/mapkit.lookaround.badgepositions)

Values that control the positions of a badge on a Look Around preview.

### [Controlling the LookAround dialog](/documentation/MapKitJS/mapkit.LookAroundPreview#Controlling-the-LookAround-dialog)

[`openDialog`](/documentation/mapkitjs/mapkit.lookaroundpreview/opendialog)

Creates a new Look Around preview object.

### [Getting information about the Look Around object and its state](/documentation/MapKitJS/mapkit.LookAroundPreview#Getting-information-about-the-Look-Around-object-and-its-state)

[`element`](/documentation/mapkitjs/mapkit.lookaroundpreview/element)

A property that represents the Look Around preview’s containing DOM element.

[`scene`](/documentation/mapkitjs/mapkit.lookaroundpreview/scene)

A property that represents the current location of the view.

[`padding`](/documentation/mapkitjs/mapkit.lookaroundpreview/padding)

The values that define content padding within the Look Around preview frame.

[`readyState`](/documentation/mapkitjs/mapkit.lookaroundpreview/readystate)

A property that represents the loading state of the Look Around preview object.

[`mapkit.LookAround.ReadyStates`](/documentation/mapkitjs/mapkit.lookaround.readystates)

Values that indicate the state of the Look Around object in the browser.

### [Closing and releasing a Look Around view](/documentation/MapKitJS/mapkit.LookAroundPreview#Closing-and-releasing-a-Look-Around-view)

[`destroy`](/documentation/mapkitjs/mapkit.lookaroundpreview/destroy)

A method you call to destroy the Look Around preview.

## [See Also](/documentation/MapKitJS/mapkit.LookAroundPreview#see-also)

### [Exploring at street level](/documentation/MapKitJS/mapkit.LookAroundPreview#Exploring-at-street-level)

[`mapkit.LookAround`](/documentation/mapkitjs/mapkit.lookaround)

A view that allows someone to see a street level view of a place.

[`LookAroundOptions`](/documentation/mapkitjs/lookaroundoptions)

Options for initializing a LookAround view.

[`LookAroundPreviewOptions`](/documentation/mapkitjs/lookaroundpreviewoptions)

Options for initializing a LookAroundPreview object.

[`mapkit.LookAroundScene`](/documentation/mapkitjs/mapkit.lookaroundscene)

Object that represents the current location of the view.

[`CommonLookAroundOptions`](/documentation/mapkitjs/commonlookaroundoptions)

Options that control the behavior of Look Around views.