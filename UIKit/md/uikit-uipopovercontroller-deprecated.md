

- UIKit
-  UIPopoverController Deprecated

Class

# UIPopoverController

An object that manages the presentation of content in a popover.

iOS 3.2–9.0DeprecatediPadOS 3.2–9.0DeprecatedMac Catalyst 13.1–13.1DeprecatedtvOSDeprecated

``` source
@MainActor
class UIPopoverController
```

Deprecated

In iOS 9 and later, a popover is implemented as a UIViewController presentation. To create a popover, UIPopoverPresentationController and specify the UIModalPresentationStyle.popover style.

## Overview

The `UIPopoverController` class is used to manage the presentation of content in a popover. You use popovers to present information temporarily. The popover content is layered on top of your existing content and the background is dimmed automatically. The popover remains visible until the user taps outside of the popover window or you explicitly dismiss it. Popover controllers are for use exclusively on iPad devices. Attempting to create one on other devices results in an exception.

To display a popover, create an instance of this class and present it using one of the appropriate methods. When initializing an instance of this class, you must specify the view controller that provides the content for the popover. Popovers normally derive their size from the view controller they present. However, you can change the size of the popover by modifying the value in the contentSize property or by calling the setContentSize(_:animated:) method. The latter approach is particularly effective if you need to animate changes to the popover’s size. The size you specify is just the preferred size for the popover’s view. The actual size may be altered to ensure that the popover fits on the screen and does not collide with the keyboard.

When displayed, taps outside of the popover window cause the popover to be dismissed automatically. To allow the user to interact with the specified views and not dismiss the popover, you can assign one or more views to the passthroughViews property. Taps inside the popover window do not automatically cause the popover to be dismissed. Your view and view controller code must handle actions and events inside the popover explicitly and call the dismiss(animated:) method as needed.

If the user rotates the device while a popover is visible, the popover controller hides the popover and then shows it again at the end of the rotation. The popover controller attempts to position the popover appropriately for you but you can also implement the popoverController(_:willRepositionPopoverTo:in:) method in the popover delegate to specify a new position.

You can assign a delegate to the popover to manage interactions with the popover and receive notifications about its dismissal. For information about the methods of the delegate object, see UIPopoverControllerDelegate.

## Topics

### Initializing the popover

init(contentViewController: UIViewController)

Returns an initialized popover controller object.

### Presenting and dismissing the popover

func present(from: CGRect, in: UIView, permittedArrowDirections: UIPopoverArrowDirection, animated: Bool)

Displays the popover and anchors it to the specified location in the view.

func present(from: UIBarButtonItem, permittedArrowDirections: UIPopoverArrowDirection, animated: Bool)

Displays the popover and anchors it to the specified bar button item.

func dismiss(animated: Bool)

Dismisses the popover programmatically.

### Configuring the popover content

var contentViewController: UIViewController

The view controller responsible for the content portion of the popover.

func setContentView(UIViewController, animated: Bool)

Sets the view controller responsible for the content portion of the popover.

var contentSize: CGSize

The size of the popover’s content view.

func setContentSize(CGSize, animated: Bool)

Changes the size of the popover’s content view.

var passthroughViews: [UIView]?

An array of views that the user can interact with while the popover is visible.

### Getting the popover attributes

var isPopoverVisible: Bool

A Boolean value indicating whether the popover is currently visible.

var arrowDirection: UIPopoverArrowDirection

The direction of the popover’s arrow.

### Accessing the delegate

var delegate: (any UIPopoverControllerDelegate)?

The delegate you want to receive popover controller messages.

### Customizing the popover appearance

var layoutMargins: UIEdgeInsets

The margins that define the portion of the screen in which it is permissible to display the popover.

var backgroundViewClass: AnyClass?

The class to use for displaying the popover background content.

var backgroundColor: UIColor?

The color of the popover’s backdrop view.

### Constants

struct UIPopoverArrowDirection

Constants for specifying the direction of the popover arrow.

## Relationships

### Inherits From

- NSObject

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSObjectProtocol
- Sendable
- UIAppearanceContainer

## See Also

### Deprecated classes

class UIActionSheet

A view that presents a set of alternatives for how to proceed with a task.

Deprecated

class UIAlertView

A view that displays an alert message.

Deprecated

class UIDocumentMenuViewController

A list of all the available document providers for a given file type and mode, in addition to custom menu items that you add.

Deprecated

class UILocalNotification

A notification that an app can schedule for presentation at a specific date and time.

Deprecated

class UIMenuController

The menu interface for the Cut, Copy, Paste, Select, Select All, and Delete commands.

Deprecated

class UIMenuItem

A custom item in the editing menu managed by the menu controller.

Deprecated

class UIMutableUserNotificationAction

A modifiable version of the user notification action class.

Deprecated

class UIMutableUserNotificationCategory

Information about custom actions that your app can perform in response to a local or push notification.

Deprecated

class UIPreviewAction

A preview action, or *peek quick action*, that displays below a peek when a user swipes the peek upward.

Deprecated

class UIPreviewActionGroup

A group of one or more child quick actions, each an instance of the preview action class.

Deprecated

class UISearchDisplayController

An object that manages the display of a search bar, along with a table view that displays search results.

Deprecated

class UIStoryboardPopoverSegue

A specific type of segue for presenting content in a popover.

Deprecated

class UIUserNotificationAction

A custom action that your app can perform in response to a remote or local notification.

Deprecated

class UIUserNotificationCategory

Information about custom actions that your app can perform in response to a local or push notification.

Deprecated

class UIUserNotificationSettings

The types of notifications that can be displayed to the user by your app.

Deprecated

