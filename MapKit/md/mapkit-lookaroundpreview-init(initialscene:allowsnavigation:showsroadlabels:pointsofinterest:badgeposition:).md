

- MapKit
- LookAroundPreview
-  init(initialScene:allowsNavigation:showsRoadLabels:pointsOfInterest:badgePosition:) 

Initializer

# init(initialScene:allowsNavigation:showsRoadLabels:pointsOfInterest:badgePosition:)

Creates a Look Around preview with an initial scene, navigation, road label, points of interest, and badge position you specify.

MapKitSwiftUIiOS 17.0+iPadOS 17.0+Mac CatalystmacOS 14.0+visionOS

``` source
@MainActor @preconcurrency
init(
    initialScene: MKLookAroundScene?,
    allowsNavigation: Bool = true,
    showsRoadLabels: Bool = true,
    pointsOfInterest: PointOfInterestCategories = .all,
    badgePosition: MKLookAroundBadgePosition = .topLeading
)
```

## Parameters 

`initialScene`  

The Look Around scene to display.

`allowsNavigation`  

A Boolean value that indicates whether the Look Around scene allows navigation after the user taps the Look Around preview to enter the full screen Look Around viewer. MapKit never allows navigation on the Look Around preview itself.

`showsRoadLabels`  

A Boolean value that indicates whether the Look Around scene shows road labels after the user taps the Look Around preview to enter the full screen Look Around viewer. MapKit never shows road labels on the Look Around preview itself.

`pointsOfInterest`  

The categories of points of interest to display after the user taps the Look Around preview to enter the full screen Look Around viewer. MapKit never displays points of interest on the Look Around preview itself. By default, MapKit displays all points of interest categories.

`badgePosition`  

A value that controls the position of a badge on the Look Around preview.

## Discussion

Navigation refers to the ability to tap-to-navigate to a different vantage point in the Look Around scene and what a person can control through the use of the `allowsNavigation` property. The framework refers to the ability to pan and zoom around the Look Around scene is as *exploring* and you can’t restrict it while in the Look Around viewer.

The Look Around viewer isn’t available on macOS and `allowsNavigation` has no effect; in iOS, exploration is always available in the Look Around viewer and you can’t disable it.

## See Also

### Creating a Look Around preview

init(scene: Binding&lt;MKLookAroundScene?>, allowsNavigation: Bool, showsRoadLabels: Bool, pointsOfInterest: PointOfInterestCategories, badgePosition: MKLookAroundBadgePosition)

Creates a Look Around preview with a binding to a scene, navigation, road label, points of interest, and badge position you specify.

