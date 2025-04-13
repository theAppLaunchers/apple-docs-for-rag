

- AppKit
- NSWindow
-  updateConstraintsIfNeeded() 

Instance Method

# updateConstraintsIfNeeded()

Updates the constraints based on changes to views in the window since the last layout.

macOS 10.7+

``` source
@MainActor
func updateConstraintsIfNeeded()
```

## Discussion

When a new layout pass is triggered for a window, the system invokes this method to ensure that any constraints for views in the window are updated with information from the current view hierarchy and its constraints. This method is called automatically by the system, but may be invoked manually if you need to examine the most up to date constraints.

Subclasses should not override this method.

## See Also

### Triggering Constraint-Based Layout

func layoutIfNeeded()

Updates the layout of views in the window based on the current views and constraints.

