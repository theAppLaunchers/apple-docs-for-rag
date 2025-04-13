

- AppKit
-  NSSearchToolbarItem 

Class

# NSSearchToolbarItem

A toolbar item that contains a search field optimized for performing text-based searches.

macOS 11.0+

``` source
@MainActor
class NSSearchToolbarItem
```

## Overview

NSSearchToolbarItem automatically resizes to accommodate typing when the focus switches to the toolbar item. When the toolbar is low on space, the system may collapse the search item into a button representation, which then expands to a full search field when the user clicks on it.

## Topics

### Configuring a search item

var preferredWidthForSearchField: CGFloat

The preferred width for the toolbar item when it has keyboard focus.

var resignsFirstResponderWithCancel: Bool

A Boolean value that enables the cancel button in the search field to resign the first responder in addition to clearing the contents.

var searchField: NSSearchField

The search field inside the toolbar item.

### Controlling search interactions

func beginSearchInteraction()

Starts a search interaction and moves the keyboard focus to the search field.

func endSearchInteraction()

Ends a search interaction by giving up the first responder and adjusting the size of the search field to the available width for the toolbar item if necessary.

## Relationships

### Inherits From

- NSToolbarItem

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSCopying
- NSMenuItemValidation
- NSObjectProtocol
- NSValidatedUserInterfaceItem
- Sendable

## See Also

### Items

class NSToolbarItem

A single item that appears in a window’s toolbar.

class NSToolbarItemGroup

A group of subitems in a toolbar item.

enum ControlRepresentation

enum SelectionMode

A value that indicates how a grouped toolbar item selects its subitems.

class NSMenuToolbarItem

A control that presents a menu in a window’s toolbar.

class NSTrackingSeparatorToolbarItem

A toolbar separator that aligns with the vertical split view in the same window.

