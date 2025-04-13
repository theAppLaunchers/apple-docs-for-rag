

- AppKit
- NSToolbarItemGroup
-  init(itemIdentifier:images:selectionMode:labels:target:action:) 

Initializer

# init(itemIdentifier:images:selectionMode:labels:target:action:)

Creates a grouped toolbar item with images.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.1+macOS 10.15+

**macOS**

``` source
@MainActor
convenience init(
    itemIdentifier: NSToolbarItem.Identifier,
    images: [NSImage],
    selectionMode: NSToolbarItemGroup.SelectionMode,
    labels: [String]?,
    target: Any?,
    action: Selector?
)
```

**Mac Catalyst**

``` source
@MainActor
convenience init(
    itemIdentifier: NSToolbarItem.Identifier,
    images: [UIImage],
    selectionMode: NSToolbarItemGroup.SelectionMode,
    labels: [String]?,
    target: Any?,
    action: Selector?
)
```

## Parameters 

`itemIdentifier`  

The identifier for the grouped toolbar item.

`images`  

An array of images to present as subitems in the grouped toolbar item.

`selectionMode`  

A value that indicates how the grouped toolbar item presents selections.

`labels`  

Labels that correspond to the specified images.

`target`  

The target that the toolbar calls upon selection.

If target is `nil`, the toolbar attempts to invoke the specified action on the first responder and, failing that, passes the action up the responder chain.

`action`  

The selector that the toolbar invokes on the target.

## See Also

### Creating grouped toolbar items

convenience init(itemIdentifier: NSToolbarItem.Identifier, titles: [String], selectionMode: NSToolbarItemGroup.SelectionMode, labels: [String]?, target: Any?, action: Selector?)

Creates a grouped toolbar item with labels.

