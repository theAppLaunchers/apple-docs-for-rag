

- AppKit
- NSViewController
-  viewDidDisappear() 

Instance Method

# viewDidDisappear()

Called after the view controller’s view is removed from the view hierarchy in a window.

macOS 10.10+

``` source
@MainActor
func viewDidDisappear()
```

## Discussion

You can override this method to perform tasks associated with removing the view controller’s view from the window’s view hierarchy, such as releasing resources not needed when the view is not visible or no longer part of the window.

If you override this method, call this method on `super` at some point in your implementation in case a superclass also overrides this method.

The default implementation of this method does nothing.

## See Also

### Responding to View Events

func viewDidLoad()

Called after the view controller’s view has been loaded into memory.

func loadViewIfNeeded()

var isViewLoaded: Bool

A Boolean value indicating whether the view controller’s view is loaded into memory.

var viewIfLoaded: NSView?

func viewWillAppear()

Called after the view controller’s view has been loaded into memory is about to be added to the view hierarchy in the window.

func viewDidAppear()

Called when the view controller’s view is fully transitioned onto the screen.

func viewWillDisappear()

Called when the view controller’s view is about to be removed from the view hierarchy in the window.

