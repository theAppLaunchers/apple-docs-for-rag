

- SpriteKit
-  SKReferenceNode 

Class

# SKReferenceNode

A node that’s defined in an archived `.sks` file.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+macOS 10.11+tvOS 9.0+visionOS 1.0+watchOS 2.0+

**iOS, iPadOS, Mac Catalyst, macOS, tvOS, visionOS**

``` source
@MainActor
class SKReferenceNode
```

**watchOS**

``` source
class SKReferenceNode
```

## Mentioned in 

Using Base Nodes to Lay Out SpriteKit Content

## Overview

`SKReferenceNode` is used within an archived `.sks` file to refer to node defined in another `.sks` file without duplicating its definition. This way, a change to the referenced node propagates to all the references in other files.

Note

`SKReferenceNode` is mostly used in conjunction with Xcode’s SpriteKit Scene editor, but it’s possible to instantiate it yourself and use the resolve() function as a handy way to restore a node’s appearance.

As an example, you might want to share an enemy ship across two different levels, Scene1.sks and Scene2.sks, in a level-based game. Reference nodes allow you to do that without creating copies of the shared node and its properties.

To use a reference node:

- Create the shared content in a separate archive

- Add references to the shared archive within your scene archives

When each scene is loaded, the reference nodes are resolved dynamically, and therefore you only need to configure a shared object in one place.

## Topics

### Initializers

convenience init(url: URL)

Creates a reference node from a URL.

init(url: URL?)

Initializes a reference node from a URL.

convenience init(fileNamed: String)

Creates a reference node from a file in the app’s main bundle.

init(fileNamed: String?)

Initializes a reference node from a file in the app’s main bundle.

init?(coder: NSCoder)

A method that initializes a reference node from an archive.

### Regenerating

Load a reference nodes contents freshly from the archive again.

func resolve()

Loads the reference node’s content and adds it as a new child node.

### Loading Callback

func didLoad(SKNode?)

A method called by SpriteKit after the reference node’s contents are loaded.

## Relationships

### Inherits From

- SKNode

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
- NSStandardKeyBindingResponding
- NSTouchBarProvider
- NSUserActivityRestoring
- Sendable
- UIActivityItemsConfigurationProviding
- UICoordinateSpace
- UIFocusEnvironment
- UIFocusItem
- UIFocusItemContainer
- UIPasteConfigurationSupporting
- UIResponderStandardEditActions
- UIUserActivityRestoring

## See Also

### Base Nodes

Using Base Nodes to Lay Out SpriteKit Content

Use nonvisual nodes to define the layout of a scene.

class SKNode

The base class of all SpriteKit nodes.

class SKCameraNode

A node that determines which parts of the scene are visible within a view.

