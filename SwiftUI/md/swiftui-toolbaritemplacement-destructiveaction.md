

- SwiftUI
- ToolbarItemPlacement
-  destructiveAction 

Type Property

# destructiveAction

The item represents a destructive action for a modal interface.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+macOS 11.0+tvOS 14.0+visionOS 1.0+watchOS 7.0+

``` source
static let destructiveAction: ToolbarItemPlacement
```

## Discussion

Destructive actions represent the opposite of a confirmation action. For example, a button labeled “Don’t Save” that allows the user to discard unsaved changes to a document before quitting.

In macOS and in Mac Catalyst apps, the system places `destructiveAction` items in the leading edge of the sheet and gives them a special appearance to caution against accidental use.

In iOS, tvOS, and watchOS, the system places `destructiveAction` items in the trailing edge of the navigation bar.

## See Also

### Getting placement for specific actions

static let primaryAction: ToolbarItemPlacement

The item represents a primary action.

static let secondaryAction: ToolbarItemPlacement

The item represents a secondary action.

static let confirmationAction: ToolbarItemPlacement

The item represents a confirmation action for a modal interface.

static let cancellationAction: ToolbarItemPlacement

The item represents a cancellation action for a modal interface.

static let navigation: ToolbarItemPlacement

The item represents a navigation action.

