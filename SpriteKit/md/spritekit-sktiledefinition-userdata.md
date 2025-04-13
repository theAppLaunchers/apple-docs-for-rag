

- SpriteKit
- SKTileDefinition
-  userData 

Instance Property

# userData

A dictionary containing arbitrary data.

iOS 10.0+iPadOS 10.0+Mac Catalyst 13.1+macOS 10.12+tvOS 10.0+visionOS 1.0+watchOS 3.0+

``` source
var userData: NSMutableDictionary? { get set }
```

## Discussion

You use this property to store your own data in a tile definition. For example, you might use this property to specify whether this tile is a platform that a player can land on.

SpriteKit doesn’t do anything with this data. However, the data is archived when the tile definition is archived.

