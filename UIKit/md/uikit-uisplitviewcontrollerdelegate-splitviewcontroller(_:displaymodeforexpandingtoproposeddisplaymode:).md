

- UIKit
- UISplitViewControllerDelegate
-  splitViewController(\_:displayModeForExpandingToProposedDisplayMode:) 

Instance Method

# splitViewController(\_:displayModeForExpandingToProposedDisplayMode:)

Asks the delegate to provide the display mode to use after the split view interface expands.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+tvOS 14.0+visionOS 1.0+

``` source
@MainActor
optional func splitViewController(
    _ svc: UISplitViewController,
    displayModeForExpandingToProposedDisplayMode proposedDisplayMode: UISplitViewController.DisplayMode
) -> UISplitViewController.DisplayMode
```

## Parameters 

`svc`  

The split view controller whose interface is expanding.

`proposedDisplayMode`  

The proposed display mode to expand the interface to.

## Return Value

The display mode to expand the interface to. This value may be the same as `proposedDisplayMode`, or you may return a different value.

## Discussion

This delegate method only applies to column-style split view interfaces. For more information, see Split view styles.

When the split view controller transitions from a horizontally compact to a horizontally regular size class, it calls this method and asks you for the display mode to use when that transition is complete. Use this method to customize the display mode you’re expanding to. For example, you might use this opportunity to adjust column widths before returning the display mode to use.

## See Also

### Expanding the interface

func splitViewController(UISplitViewController, willShow: UISplitViewController.Column)

Tells the delegate that the specified column is about to be shown.

func splitViewControllerDidExpand(UISplitViewController)

Tells the delegate that the split view controller interface has expanded.

