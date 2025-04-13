

- SwiftData
- ModelContext
-  processPendingChanges() 

Instance Method

# processPendingChanges()

Tells the undo manager to record any changes made to the context’s registered models.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+tvOS 17.0+visionOS 1.0+watchOS 10.0+Swift 5.9+

``` source
func processPendingChanges()
```

## Discussion

In AppKit-based applications, the system invokes this method at the end of each event loop. The framework may call it more frequently if it needs to coalesce your changes before continuing. You can also invoke it manually to coalesce any pending changes.

## See Also

### Performing undo and redo

var undoManager: UndoManager?

The object that provides undo support for the context.

