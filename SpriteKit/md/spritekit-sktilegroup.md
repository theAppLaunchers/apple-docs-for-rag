

- SpriteKit
-  SKTileGroup 

Class

# SKTileGroup

A set of tiles that collectively define one type of terrain.

iOS 10.0+iPadOS 10.0+Mac Catalyst 13.1+macOS 10.12+tvOS 10.0+visionOS 1.0+watchOS 3.0+

``` source
class SKTileGroup
```

## Overview

An `SKTileGroup` object contains either the definition of a single tile or an array of SKTileGroupRule objects that define adjacency rules.

You supply a tile group with either:

- The definition of a single tile that can be used to populate a tile map node with a single texture.

- An array of one or more tile group rules that allow for the automatic placement of textures dependent on their adjacency and the placement weights of their definitions. For example, a tile group may contain nine tile group rules containing the definitions of the central tile and eight edge tiles that, when placed adjacently, appear as a single object.

The preferred method to create tile groups is to use the editor tools in Xcode. However, to work with SpriteKit’s tile support programmatically, see the following articles.

## Topics

### Creating Tile Groups

Creating Tile Groups Programmatically

Paint tiles on a map by putting tile definitions in a group that you create in code.

init(tileDefinition: SKTileDefinition)

Creates and initializes a simple tile group with a single tile definition.

init(rules: [SKTileGroupRule])

Creates and initializes a tile group with the specified tile group rules.

### Accessing or Setting a Tile Group’s Properties

var name: String?

The receiver’s name.

var rules: [SKTileGroupRule]

An array of SKTileGroupRule objects that the tile group uses to determine tile placement.

### Creating an Empty Tile Group

Create an empty tile group to erase tiles at a given location on a map.

class func empty() -> Self

Creates an empty tile that erases the existing tile at that location on a tile map.

## Relationships

### Inherits From

- NSObject

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSCoding
- NSCopying
- NSObjectProtocol
- NSSecureCoding

## See Also

### Tiling

class SKTileMapNode

A two-dimensional array of images.

class SKTileDefinition

A single tile that can be repeated in a tile map.

class SKTileGroupRule

Rules that describe how various tiles should be placed in a map.

class SKTileSet

A container for related tile groups.

