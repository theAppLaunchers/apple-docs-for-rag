

- MapKit
- MKTileOverlay
-  maximumZ 

Instance Property

# maximumZ

The maximum zoom level that the tiles of this overlay object support.

iOS 7.0+iPadOS 7.0+Mac Catalyst 13.1+macOS 10.9+tvOS 9.2+visionOS 1.0+

``` source
var maximumZ: Int { get set }
```

## Discussion

If you use different overlay objects to represent different tiles at different zoom levels, use this property to specify the maximum zoom level that this overlay’s tiles support. At zoom level 0, tiles cover the entire world map; at zoom level 1, tiles cover 1/4 of the world; at zoom level 2, tiles cover 1/16 of the world, and so on. The map doesn’t attempt to load tiles for a zoom level greater than the value that this property specifies.

The default value of this property is `21`. Setting the value of this property to a number greater than the default doesn’t ensure the use of those extra zoom levels.

## See Also

### Accessing the tile attributes

var tileSize: CGSize

The size (in pixels) of your tile images.

var isGeometryFlipped: Bool

A Boolean value that indicates the orientation of tile indexes along the y-axis.

var minimumZ: Int

The minimum zoom level that the tiles of this overlay object support.

var canReplaceMapContent: Bool

A Boolean value that indicates whether the tile content is fully opaque.

