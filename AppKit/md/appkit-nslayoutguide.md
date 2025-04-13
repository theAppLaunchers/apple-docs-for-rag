

- AppKit
-  NSLayoutGuide 

Class

# NSLayoutGuide

A rectangular area that can interact with Auto Layout.

macOS 10.11+

``` source
class NSLayoutGuide
```

## Overview

Use layout guides to replace the placeholder views you may have created to represent inter-view spaces or encapsulation in your user interface. Traditionally, there were a number of Auto Layout techniques that required placeholder views. A placeholder view is an empty view that does not have any visual elements of its own and serves only to define a rectangular region in the view hierarchy. For example, if you wanted to use constraints to define the size or location of an empty space between views, you needed to use a placeholder view to represent that space. If you wanted to center a group of objects, you needed a placeholder view to contain those objects. Similarly, placeholder views could be used to contain and encapsulate part of your user interface. Placeholder views let you break up a large, complex user interface into self-contained, modular chunks. When used properly, they could greatly simplify your Auto Layout constraint logic.

There are a number of costs associated with adding placeholder views to your view hierarchy. First, there is the cost of creating and maintaining the view itself. Second, the placeholder view is a full member of the view hierarchy, which means that it adds overhead to every task the hierarchy performs. Worst of all, the invisible placeholder view can intercept messages that are intended for other views, causing problems that are very difficult to find.

The NSLayoutGuide class is designed to perform all the tasks previously performed by placeholder views, but to do it in a safer, more efficient manner. Layout guides are not views. They do not use as much memory, and they do not participate in the view hierarchy. Instead, they simply define a rectangular region in their owning view’s coordinate system that can interact with Auto Layout.

### Creating Layout Guides

To create a layout guide, perform the following steps:

1.  Instantiate a new layout guide.

2.  Add the layout guide to a view by calling the view’s addLayoutGuide(_:) method .

3.  Define the position and size of the layout guide using Auto Layout.

You can use these guides to define the space between elements in your layout. The following example shows how to use layout guides to define an equal spacing between a series of views.

- Swift
- Objective-C

```
let space1 = NSLayoutGuide()
view.addLayoutGuide(space1)

let space2 = NSLayoutGuide()
view.addLayoutGuide(space2)

space1.widthAnchor.constraintEqualToAnchor(space2.widthAnchor).active = true
saveButton.trailingAnchor.constraintEqualToAnchor(space1.leadingAnchor).active = true
cancelButton.leadingAnchor.constraintEqualToAnchor(space1.trailingAnchor).active = true
cancelButton.trailingAnchor.constraintEqualToAnchor(space2.leadingAnchor).active = true
clearButton.leadingAnchor.constraintEqualToAnchor(space2.trailingAnchor).active = true
```

```
NSLayoutGuide *space1 = [[NSLayoutGuide alloc]init];
[self.view addLayoutGuide:space1];

NSLayoutGuide *space2 = [[NSLayoutGuide alloc] init];
[self.view addLayoutGuide:space2];

[space1.widthAnchor constraintEqualToAnchor:space2.widthAnchor].active = YES;
[self.saveButton.trailingAnchor constraintEqualToAnchor:space1.leadingAnchor].active = YES;
[self.cancelButton.leadingAnchor constraintEqualToAnchor:space1.trailingAnchor].active = YES;
[self.cancelButton.trailingAnchor constraintEqualToAnchor:space2.leadingAnchor].active = YES;
[self.clearButton.leadingAnchor constraintEqualToAnchor:space2.trailingAnchor].active = YES;
```

A layout guide can also act as an opaque box that contains other views and controls, letting you encapsulate parts of your view and break up your layout into modular chunks.

- Swift
- Objective-C

```
let container = NSLayoutGuide()
view.addLayoutGuide(container)

// Layout the contents of the container
button.lastBaselineAnchor.constraintEqualToAnchor(textField.lastBaselineAnchor).active = true
button.leadingAnchor.constraintEqualToAnchor(container.leadingAnchor).active = true
textField.leadingAnchor.constraintEqualToAnchor(button.trailingAnchor, constant: 8.0).active = true
textField.trailingAnchor.constraintEqualToAnchor(container.trailingAnchor).active = true
textField.topAnchor.constraintEqualToAnchor(container.topAnchor).active = true
textField.bottomAnchor.constraintEqualToAnchor(container.bottomAnchor).active = true

// Set exterior constraints.
container.leadingAnchor.constraintEqualToAnchor(margins.leadingAnchor).active = true
container.trailingAnchor.constraintEqualToAnchor(margins.trailingAnchor).asctive = true
container.topAnchor.constraintEqualToAnchor(margins.topAnchor).active = true
```

```
NSLayoutGuide *container = [[NSLayoutGuide alloc] init];
[self.view addLayoutGuide:container];

// Layout the contents of the container
[self.button.lastBaselineAnchor constraintEqualToAnchor:self.textField.lastBaselineAnchor].active = YES;
[self.textField.leadingAnchor constraintEqualToAnchor:self.button.trailingAnchor constant:8.0].active = YES;
[self.textField.trailingAnchor constraintEqualToAnchor:container.trailingAnchor].active = YES;
[self.textField.topAnchor constraintEqualToAnchor:container.topAnchor].active = YES;
[self.textField.bottomAnchor constraintEqualToAnchor:container.bottomAnchor].active = YES;

// Set exterior constraints.

[container.leadingAnchor constraintEqualToAnchor:self.view.leadingAnchor constant:20.0].active = YES;
[container.trailingAnchor constraintEqualToAnchor:self.view.trailingAnchor constant:20.0].active = YES;
[container.topAnchor constraintEqualToAnchor:self.view.topAnchor constant:20.0].active = YES;
```

Note

Layout constraints do not fully encapsulate their contents. The system still compares the priority of optional constraints inside the layout guide with the priority of optional constraints outside the guide.

## Topics

### Working With Layout Guides

var identifier: NSUserInterfaceItemIdentifier

A string used to identify the layout guide.

var frame: NSRect

The layout guide’s frame in its owning view’s coordinate system.

var owningView: NSView?

The view that owns this layout guide.

### Creating Constraints Using Layout Anchors

var bottomAnchor: NSLayoutYAxisAnchor

A layout anchor representing the bottom edge of the layout guide’s frame.

var centerXAnchor: NSLayoutXAxisAnchor

A layout anchor representing the horizontal center of the layout guide’s frame.

var centerYAnchor: NSLayoutYAxisAnchor

A layout anchor representing the vertical center of the layout guide’s frame.

var heightAnchor: NSLayoutDimension

A layout anchor representing the height of the layout guide’s frame.

var leadingAnchor: NSLayoutXAxisAnchor

A layout anchor representing the leading edge of the layout guide’s frame.

var leftAnchor: NSLayoutXAxisAnchor

A layout anchor representing the left edge of the layout guide’s frame.

var rightAnchor: NSLayoutXAxisAnchor

A layout anchor representing the right edge of the layout guide’s frame.

var topAnchor: NSLayoutYAxisAnchor

A layout anchor representing the top edge of the layout guide’s frame.

var trailingAnchor: NSLayoutXAxisAnchor

A layout anchor representing the trailing edge of the layout guide’s frame.

var widthAnchor: NSLayoutDimension

A layout anchor representing the width of the layout guide’s frame.

### Instance Properties

var hasAmbiguousLayout: Bool

### Instance Methods

func constraintsAffectingLayout(for: NSLayoutConstraint.Orientation) -> [NSLayoutConstraint]

## Relationships

### Inherits From

- NSObject

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSCoding
- NSObjectProtocol
- NSUserInterfaceItemIdentification

## See Also

### Layout Guides

class NSLayoutDimension

A factory class for creating size-based layout constraint objects using a fluent API.

