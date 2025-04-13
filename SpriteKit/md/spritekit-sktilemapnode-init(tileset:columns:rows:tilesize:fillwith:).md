

- SpriteKit
- SKTileMapNode
-  init(tileSet:columns:rows:tileSize:fillWith:) 

Initializer

# init(tileSet:columns:rows:tileSize:fillWith:)

Creates and initializes a tile map node using the provided tile set with a specified number of columns and rows.

iOS 10.0+iPadOS 10.0+Mac Catalyst 13.1+macOS 10.12+tvOS 10.0+visionOS 1.0+watchOS 3.0+

**watchOS**

``` source
init(
    tileSet: SKTileSet,
    columns: Int,
    rows: Int,
    tileSize: CGSize,
    fillWith tileGroup: SKTileGroup
)
```

**iOS, iPadOS, Mac Catalyst, macOS, tvOS, visionOS**

``` source
@MainActor
init(
    tileSet: SKTileSet,
    columns: Int,
    rows: Int,
    tileSize: CGSize,
    fillWith tileGroup: SKTileGroup
)
```

## Parameters 

`tileSet`  

The tile set that is used to render the tiles.

`columns`  

The number of columns in the map.

`rows`  

The number of rows in the map.

`tileSize`  

The size of each tile in points.

`tileGroup`  

The tile group to fill the tile map with.

## Return Value

A new tile map node.

## Discussion

For a grid set type, the overall size, in points, of the node will be `numberOfColumns` \* `tileSize.width` wide and `numberOfRows` \* `tileSize.height` high. This initializer fills each tile with a texture defined by the descriptors in the final `SKTileGroup` argument.

## See Also

### Creating a Tile Map

init(tileSet: SKTileSet, columns: Int, rows: Int, tileSize: CGSize)

Creates and initializes a tile map node using the provided tile set with a specified number of columns and rows.

init(tileSet: SKTileSet, columns: Int, rows: Int, tileSize: CGSize, tileGroupLayout: [SKTileGroup])

Creates and initializes a tile map node using the provided tile set with a specified number of columns and rows. For a grid set type, the overall size, in points, of the node will be `numberOfColumns * tileSize.width` wide and `numberOfRows * tileSize.height` high.

class func tileMapNodes(tileSet: SKTileSet, columns: Int, rows: Int, tileSize: CGSize, from: GKNoiseMap, tileTypeNoiseMapThresholds: [NSNumber]) -> [SKTileMapNode]

Creates a tile map node by allowing a GKNoiseMap to choose its tiles.

