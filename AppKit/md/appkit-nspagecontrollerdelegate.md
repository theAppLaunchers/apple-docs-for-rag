

- AppKit
-  NSPageControllerDelegate 

Protocol

# NSPageControllerDelegate

The `NSPageControllerDelegate` protocol allows you to customize the behavior of instances of the NSPageController class.

macOS

``` source
protocol NSPageControllerDelegate : NSObjectProtocol
```

## Overview

See NSPageController for more information.

Note

If your page controller is going to completely manage the page snapshots, then you should not implement the pageController(_:viewControllerForIdentifier:) or pageController(_:prepare:with:) methods.

However, if you manually set the `NSPageController` instance’s arrangedObjects property, you are required to implement the following those methods so that navigation can properly occur.

## Topics

### Transition Notification

func pageControllerWillStartLiveTransition(NSPageController)

This message is sent when the user begins a transition.

func pageControllerDidEndLiveTransition(NSPageController)

This message is sent when a transition animation completes.

func pageController(NSPageController, didTransitionTo: Any)

This message is sent when any page transition is completed.

### Managing View Controllers

func pageController(NSPageController, identifierFor: Any) -> NSPageController.ObjectIdentifier

Return the identifier of the view controller that owns a view to display the object.

func pageController(NSPageController, viewControllerForIdentifier: NSPageController.ObjectIdentifier) -> NSViewController

Returns a view controller the page controller uses for managing the specified identifier.

func pageController(NSPageController, prepare: NSViewController, with: Any?)

Prepare the view controller and it’s view for drawing.

func pageController(NSPageController, frameFor: Any?) -> NSRect

Returns the frame appropriate for displaying the specified object.

typealias ObjectIdentifier

## Relationships

### Inherits From

- NSObjectProtocol

## See Also

### Customizing the Paged Interface Behavior

var delegate: (any NSPageControllerDelegate)?

The page controller’s delegate object.

