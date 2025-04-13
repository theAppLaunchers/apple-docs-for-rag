

- UIKit
- Drag and drop
-  Making a view into a drag source 

Article

# Making a view into a drag source

Adopt drag interaction APIs to provide items for dragging.

iOS 11.0+iPadOS 11.0+

## Overview

By implementing a drag interaction delegate (UIDragInteractionDelegate) for a view, you enable that view to function as a drag source in your app.

Note

The UITextView, UITableView, and UICollectionView classes each provide their own, specialized support for creating drag items. See these classes for more information.

### Enable a view as a drag source

Any instance or subclass of UIView can act as a drag source. Your first steps to make this happen are:

1.  Create a drag interaction (a UIDragInteraction instance).

2.  Specify the drag interaction’s delegate (an object that conforms to the UIDragInteractionDelegate protocol).

3.  Add the interaction to the view’s interactions property.

Here’s how to do this using a custom helper method, which you’d typically call within a view controller’s viewDidLoad() method:

```
func customEnableDragging(on view: UIView, dragInteractionDelegate: UIDragInteractionDelegate) {
    let dragInteraction = UIDragInteraction(delegate: dragInteractionDelegate)
    view.addInteraction(dragInteraction)
}
```

### Create a drag item

A drag item encapsulates a source app’s promises for providing a variety of data representations for one model object.

To create a drag item, implement the dragInteraction(_:itemsForBeginning:) method in your drag interaction delegate, as shown here in a minimal form:

```
func dragInteraction(_ interaction: UIDragInteraction, itemsForBeginning session: UIDragSession) -> [UIDragItem] {
    // Cast to NSString is required for NSItemProviderWriting support.
    let stringItemProvider = NSItemProvider(object: "Hello World" as NSString)
    return [
        UIDragItem(itemProvider: stringItemProvider)
    ]
}
```

Note

The cast from the Swift String type to the Foundation NSString class, in the code snippet above, is required because model objects for drag and drop must support the NSItemProviderWriting protocol.

This implementation uses the init(object:) convenience initializer. When you instantiate a drag item, pass an object in your app’s native representation, or in the highest-fidelity representation you support. In general, ensure that the first element in the item provider’s registeredTypeIdentifiers array represents the highest-fidelity data your drag interaction delegate can deliver.

To add more data representations to a drag item, as you typically would in your app, add them in fidelity order, from highest to lowest. When adding representations, you have choices:

- The best option for adding multiple data representations to a drag item, in many cases, is to adopt the NSItemProviderWriting protocol in your model class. Using this protocol, you place the code for providing multiple data representations within the model class.

- You can use the registerObject(_:visibility:) method, or related methods, from the NSItemProvider class, to explicitly register data representations.

### Understand a drag source in context

In the dragInteraction(_:itemsForBeginning:) protocol method, your source app responds to a request from the system. This request is itself triggered by the user starting to drag an item in your app’s UI. The conversation between your app and the system proceeds as shown here:

The figure above depicts the steps for constructing a drag item, in context:

1.  The user initiates a drag activity with a long press on a view in your app, followed by moving their finger while still touching the screen. The system instantiates a drag session (an object that conforms to the UIDragSession protocol, not shown in the figure) for managing the drag activity.

2.  The system calls the drag interaction delegate’s dragInteraction(_:itemsForBeginning:) protocol method. Your delegate returns one or more drag items.

3.  Finally, the system populates the drag session with your drag items, ready for the user to move the drag session to a destination.

## See Also

### Essentials

Understanding a drag item as a promise

Use drag items to convey data representation promises between a source app and a destination app.

Making a view into a drop destination

Adopt drop interaction APIs to selectively consume dragged content.

Adopting drag and drop in a custom view

Demonstrates how to enable drag and drop for a `UIImageView` instance.

Adopting drag and drop in a table view

Demonstrates how to enable and implement drag and drop for a table view.

