*   [MapKit JS](/documentation/mapkitjs)
*   mapkit.LookAround

Class

# mapkit.LookAround

A view that allows someone to see a street level view of a place.

MapKit JS 5.79+

```swift
```swift
```swift
```swift
```swift
```swift
```

```
interface mapkit.LookAround
```

```
```
```
```
```
```
```

## [Mentioned in](/documentation/MapKitJS/mapkit.LookAround#mentions)

[

Loading the latest version of MapKit JS](/documentation/mapkitjs/loading-the-latest-version-of-mapkit-js)

[

MapKit JS 5](/documentation/mapkitjs/mapkit-js-5)

## [Discussion](/documentation/MapKitJS/mapkit.LookAround#Discussion)

Note

The full bundle of MapKit JS doesn’t implement this class.

Use a Look Around view to create street level imagery for a specific geographic location on the map. You can, optionally, enable someone to navigate inside this view to allow them to explore the place at street level or zoom the view for a larger screen experience.

Note

Not all places support Look Around.

The following example contains the two elements needed to display a Look Around View on a web page:

![A screenshot showing the Look Around view framing Cherry Hill Fountain, with a Point of Interest Marker.](https://docs-assets.developer.apple.com/published/e3ef0f4db9e0eb675c326ad786aad5e3/LookAround-cl-01%402x.png)

The HTML code below implements a web page that renders a `container` which has a label that provides a description of the place the Look Around view displays.

```

```
<script
  src="https://cdn.apple-mapkit.com/mk/5.x.x/mapkit.core.js"
  crossorigin async
  data-callback="initMapKit"
  data-token="YOUR TOKEN HERE"
  data-libraries="look-around,services"></script>
<style>
#container { width: 735px; height: 552px }
</style>
<div id="container"></div>
```

```

The JavaScript listing below implements a MapKitJS Look Around object that the web page displays inside the `<div id="container">` element of the page. The Look Around view shows a navigable view of Cherry Hill Fountain in Central Park in New York City that Look Around renders using a PlaceID. For more information on obtaining a PlaceID for a specific location. For more information on Place IDs, see [Identifying unique locations with Place IDs](https://developer.apple.com/maps/place-id-lookup/).

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
          // The PlaceID that represents Cherry Hill Fountain, Central Park, New York, NY
          "IEA18943388D2216C",
          (error, result) => resolve(result)
      )
  );
  // Create an interactive look around view.
  const lookAround = new mapkit.LookAround(
      document.getElementById("container"),
      place,
      {
          // Allow users to expand the view.
          showsDialogControl: true
      }
  );
})()
```

```

## [Handling Look Around loading states](/documentation/MapKitJS/mapkit.LookAround#Handling-Look-Around-loading-states)

Look Around view dispatches the following events:

*   `load`: Look Around view is loaded.
    
*   `error`: Look Around view has encountered an error, for example, in an unsupported browser, or a location with no look around imagery.
    
*   `readystatechange`: [`readyState`](/documentation/mapkitjs/mapkit.lookaround/readystate) has changed.
    
*   `open-dialog`: Look Around view is about to expand.
    
*   `leave-dialog`: Look Around view is about to contract.
    
*   `close`: The user has interacted with the close control.
    

## [Topics](/documentation/MapKitJS/mapkit.LookAround#topics)

### [Creating a Look Around view](/documentation/MapKitJS/mapkit.LookAround#Creating-a-Look-Around-view)

[`mapkit.LookAround`](/documentation/mapkitjs/mapkit.lookaround/mapkit.lookaround)

Creates a Look Around object you embed on a webpage and initializes it with the constructor options you choose.

### [Controlling the interactions with a Look Around view](/documentation/MapKitJS/mapkit.LookAround#Controlling-the-interactions-with-a-Look-Around-view)

[`isNavigationEnabled`](/documentation/mapkitjs/mapkit.lookaround/isnavigationenabled)

A Boolean value that indicates whether someone can navigate inside the Look Around view.

[`isScrollEnabled`](/documentation/mapkitjs/mapkit.lookaround/isscrollenabled)

A Boolean value that indicates whether someone can scroll the Look Around view.

[`isZoomEnabled`](/documentation/mapkitjs/mapkit.lookaround/iszoomenabled)

A Boolean value that indicates whether someone can zoom the Look Around view.

### [Controlling additional information the Look Around view displays](/documentation/MapKitJS/mapkit.LookAround#Controlling-additional-information-the-Look-Around-view-displays)

[`showsPointsOfInterest`](/documentation/mapkitjs/mapkit.lookaround/showspointsofinterest)

A Boolean value that indicates whether the Look Around view shows points of interest (POIs).

[`showsRoadLabels`](/documentation/mapkitjs/mapkit.lookaround/showsroadlabels)

A Boolean value that indicates whether the Look Around view shows road labels.

### [Controlling the Look Around dialog](/documentation/MapKitJS/mapkit.LookAround#Controlling-the-Look-Around-dialog)

[`openDialog`](/documentation/mapkitjs/mapkit.lookaround/opendialog)

A Boolean value that indicates whether to expand the Look Around view.

### [Controlling the display of window controls](/documentation/MapKitJS/mapkit.LookAround#Controlling-the-display-of-window-controls)

[`showsCloseControl`](/documentation/mapkitjs/mapkit.lookaround/showsclosecontrol)

A Boolean value that indicates whether the Look Around view displays a close control.

[`showsDialogControl`](/documentation/mapkitjs/mapkit.lookaround/showsdialogcontrol)

A Boolean value that indicates whether the Look Around view displays shows a control that allow someone to expand the Look Around view.

### [Getting information about the Look Around object and its state](/documentation/MapKitJS/mapkit.LookAround#Getting-information-about-the-Look-Around-object-and-its-state)

[`element`](/documentation/mapkitjs/mapkit.lookaround/element)

A property that represents the Look Around view’s containing DOM element.

[`scene`](/documentation/mapkitjs/mapkit.lookaround/scene)

A property that represents the current location of the view.

[`padding`](/documentation/mapkitjs/mapkit.lookaround/padding)

The values that define content padding within the Look Around view’s frame.

[`readyState`](/documentation/mapkitjs/mapkit.lookaround/readystate)

A value that represents the loading state of the Look Around object.

[`mapkit.LookAround.ReadyStates`](/documentation/mapkitjs/mapkit.lookaround.readystates)

Values that indicate the state of the Look Around object in the browser.

### [Closing and releasing a Look Around view](/documentation/MapKitJS/mapkit.LookAround#Closing-and-releasing-a-Look-Around-view)

[`destroy`](/documentation/mapkitjs/mapkit.lookaround/destroy)

A method you call to destroy the Look Around view.

## [See Also](/documentation/MapKitJS/mapkit.LookAround#see-also)

### [Exploring at street level](/documentation/MapKitJS/mapkit.LookAround#Exploring-at-street-level)

[`LookAroundOptions`](/documentation/mapkitjs/lookaroundoptions)

Options for initializing a LookAround view.

[`mapkit.LookAroundPreview`](/documentation/mapkitjs/mapkit.lookaroundpreview)

A class that renders a preview of a LookAround view.

[`LookAroundPreviewOptions`](/documentation/mapkitjs/lookaroundpreviewoptions)

Options for initializing a LookAroundPreview object.

[`mapkit.LookAroundScene`](/documentation/mapkitjs/mapkit.lookaroundscene)

Object that represents the current location of the view.

[`CommonLookAroundOptions`](/documentation/mapkitjs/commonlookaroundoptions)

Options that control the behavior of Look Around views.