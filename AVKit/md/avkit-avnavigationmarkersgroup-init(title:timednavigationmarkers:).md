

- AVKit
- AVNavigationMarkersGroup
-  init(title:timedNavigationMarkers:) 

Initializer

# init(title:timedNavigationMarkers:)

Initializes a navigation markers group with the specified title and array of timed navigation markers.

tvOS 9.0+

``` source
init(
    title: String?,
    timedNavigationMarkers navigationMarkers: [AVTimedMetadataGroup]
)
```

## Parameters 

`title`  

The title to present for the markers group.

`navigationMarkers`  

The array of timed navigation markers for which the group provides navigation.

## Return Value

A new navigation markers group.

## Discussion

To associate marker groups with an asset for playback, use the navigationMarkerGroups property of an AVPlayerItem object.

To create a chapter list, pass `nil` for the `title` parameter and set the group as the first item in the player item’s navigationMarkerGroups array. To provide additional options for navigating media (such as a “Goals Scored” group for a recorded sporting event), provide a unique `title` value for each marker group in the array.

## See Also

### Creating a Navigation Marker Group

init(title: String?, dateRangeNavigationMarkers: [AVDateRangeMetadataGroup])

Initializes a navigation markers group with the specified title and array of date range navigation markers.

