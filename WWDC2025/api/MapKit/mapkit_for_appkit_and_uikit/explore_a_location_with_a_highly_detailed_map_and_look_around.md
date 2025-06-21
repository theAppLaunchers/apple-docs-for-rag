*   [MapKit](/documentation/mapkit)
*   [MapKit for AppKit and UIKit](/documentation/mapkit/mapkit-for-appkit-and-uikit)
*   Explore a location with a highly detailed map and Look Around

Sample Code

# Explore a location with a highly detailed map and Look Around

Display a richly detailed map, and use Look Around to experience an interactive view of landmarks.

[Download](https://docs-assets.developer.apple.com/published/693676fe6d/ExploreALocationWithAHighlyDetailedMapAndLookAround.zip)

iOS 16.0+iPadOS 16.0+Xcode 14.0+

## [Overview](/documentation/mapkit/mapkit_for_appkit_and_uikit/explore_a_location_with_a_highly_detailed_map_and_look_around#overview)

This sample code project takes the user on a tour of landmarks in San Francisco, using MapKit to do the following:

*   Show a highly detailed map, including trees, realistic elevation, and detailed building renderings for landmark locations
    
*   Navigate between landmarks, with the navigation route following the elevation of the roads and blending with landscape features
    
*   Animate the map between landmarks
    
*   Display the landmark using an interactive `MKLookAroundViewController`, as well as a snapshot of the landmark with `MKLookAroundSnapshotter`
    

Note

This sample code project is associated with WWDC22 session [10035: What’s new in MapKit](https://developer.apple.com/wwdc22/10035/).

## [See Also](/documentation/mapkit/mapkit_for_appkit_and_uikit/explore_a_location_with_a_highly_detailed_map_and_look_around#see-also)

### [Exploring at street level](/documentation/mapkit/mapkit_for_appkit_and_uikit/explore_a_location_with_a_highly_detailed_map_and_look_around#exploring-at-street-level)

```swift
```swift
```swift
```swift
```swift
class
```
 MKLookAroundScene
```
```

A utility class that encapsulates information the framework requires to retrieve and display a specific Look Around location’s imagery.
```
```swift
```swift
```swift
```swift
class
```
 MKLookAroundSceneRequest
```
```

A class you use to request a LookAround scene at the location you specify.
```
```swift
```swift
```swift
```swift
class
```
 MKLookAroundViewController
```
```

A class that manages the presentation and display of a LookAround view.
```
```swift
```swift
```swift
```swift
class
```
 MKLookAroundSnapshotter
```
```

A utility class that you use to create a static image from a LookAround scene.
```
```