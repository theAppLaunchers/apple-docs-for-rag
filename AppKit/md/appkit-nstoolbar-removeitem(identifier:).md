

- AppKit
- NSToolbar
-  removeItem(identifier:) 

Instance Method

# removeItem(identifier:)

Removes the item with matching `itemIdentifier` in the receiving toolbar. If multiple items share the same identifier (as is the case with space items) all matching items will be removed. To remove only a single space item, use `-removeItemAtIndex:` instead.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+

``` source
@MainActor
func removeItem(identifier itemIdentifier: NSToolbarItem.Identifier)
```

## Discussion

Any change made will be propagated immediately to all other toolbars with the same identifier.

