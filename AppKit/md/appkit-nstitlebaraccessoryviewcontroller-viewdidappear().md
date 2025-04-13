

- AppKit
- NSTitlebarAccessoryViewController
-  viewDidAppear() 

Instance Method

# viewDidAppear()

Called when the title bar accessory view controller’s view is fully transitioned onto the screen.

macOS 10.10+

``` source
@MainActor
func viewDidAppear()
```

## Discussion

This method is called after the completion of all drawing and animations involved in the initial appearance of the accessory view. You can override this method to perform tasks appropriate for that time—such as work that should not interfere with the presentation animation, or starting an animation that you want to begin after the view appears—but you must call `super` in your implementation.

## See Also

### Responding to View Events

func viewDidDisappear()

Called after the title bar accessory view controller’s view is removed from the window’s view hierarchy.

func viewWillAppear()

Called after the title bar accessory view controller’s view has been loaded into memory is about to be added to the view hierarchy in the window.

