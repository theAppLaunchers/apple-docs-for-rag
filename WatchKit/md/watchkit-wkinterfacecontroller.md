

- WatchKit
-  WKInterfaceController 

Class

# WKInterfaceController

A class that provides the infrastructure for managing the interface in a watchOS app.

watchOS 2.0+

``` source
@MainActor
class WKInterfaceController
```

## Overview

An interface controller serves the same purpose as a UIViewController object in a UIKit app, except that it doesn’t manage any actual views. It runs in your WatchKit extension and remotely manages the behavior associated with an interface controller in your Watch app’s storyboard file. You subclass WKInterfaceController and use its methods to configure the elements of your storyboard scene and to respond to interactions with those elements.

Your interface controller code runs locally on the user’s Apple Watch but is separate from the interface that it manages. When you change the value of an interface object in your code, the system forwards the needed information to your Watch app, which makes the corresponding changes onscreen.

### Initialize your interface controllers

When the user interacts with your app content, the system launches your extension and creates the appropriate interface controller objects automatically. Apps use different interface controllers to manage their notification and app interfaces; WatchKit uses the information in your app’s main storyboard file to determine which interface controller to load. Notification scenes are configured specially so that the system can identify them. For your app, WatchKit loads your app’s main interface controller initially, but you may change the initial interface controller at launch time.

When creating an interface controller, WatchKit instantiates the class and calls its init() method. You can use this method to initialize variables and load data; however, don’t use it to configure your user interface. The controller’s user interface elements may not be properly initialized when this method runs.

Next, the system calls the awake(withContext:) method. If WatchKit passes a valid object to the awake(withContext:) method, use the information in that object to customize the initialization process. Also, the controller’s user interface elements are guaranteed to be available at this point. This means that you can safely use this method to configure your user interface.

The willActivate() method lets you know when your interface is about to become active. Use the willActivate() method to perform any last minute tasks, such as checking for updates to your content; however, don’t use it for your primary initialization.

The willActivate() method may be called at times when your interface isn’t yet onscreen. For example, WatchKit may call the method in advance so that you have time to update your content. WatchKit calls the didAppear() method to let you know when your interface becomes visible. Similarly, WatchKit calls the willDisappear() and didDeactivate() methods when your interface moves offscreen again.

Important

An interface controller can make changes to its interface only in the awake(withContext:) method, in the willActivate() method, and while the interface is active. Once the system calls the didDeactivate() method, it ignores any attempts to change the value of the controller’s interface objects until the system calls the interface controller’s willActivate() method again.

In iOS Simulator, WatchKit calls the didDeactivate() method for the current interface controller when you lock the simulator by selecting Hardware \> Lock. When you subsequently unlock the simulator, WatchKit calls that interface controller’s willActivate() method again. You can use this capability to debug your activation and deactivation code.

### Interface Builder configuration options

Xcode lets you configure information about your interface controller in your storyboard file. The following table lists the attributes you can configure in your storyboard and their meaning.

| Attribute | Description |
|----|----|
| Identifier | The name of the interface controller. Use this name to specify which interface controller to push or present. |
| Title | The title string assigned to the interface controller. You can set this value programmatically using the setTitle(_:) method. |
| Is Initial Controller | A Boolean indicating whether the object is the app’s root interface controller. Only one interface controller at a time may have this option enabled. This option doesn’t apply to glance or notification interface controllers. |
| Activity Indicator On Load | A Boolean value that indicates whether the interface controller’s contents are hidden until the willActivate() method returns. When you enable this option, the system displays a progress indicator until the willActivate() method returns. You might disable this option if your interface contains mostly static information that can be displayed right away. |
| Always Bounce | A Boolean value that turns off scrolling and allows built-in controls and containers to fill content to the screen edges, regardless of the content-safe area. |
| Full Screen | A Boolean value that determines whether SpriteKit or SceneKit content can use the full screen. The system hides the status bar but displays the time in the upper-right corner with a gradient behind it, making the time clearly visible against the scene. |
| Fixed to screen edges | A Boolean value that indicates whether the contents ignore the safe area and minimum layout margins. When you enable this option, the system turns off scrolling, and allows built-in controls and containers to fill content to the screen edges. |
| Background | The background image displayed behind the scene’s content. The image specified in your storyboard scrolls with your interface controller’s content. |
| Mode | The content mode for the background image. This mode defines how the background image scales or fills the screen and behaves in the same way as the constants for the UIView.ContentMode type. |
| Animate | A Boolean value indicating whether an animated background image starts running its animation automatically after being loaded. Set this option to `Yes` if you want the animation to start automatically; set it to `No` if you prefer to start the animation programmatically. |
| Color | The background color to be displayed behind the scene’s content. |
| Insets | The amount of space (in points) to insert between the edges of the interface controller and its content. Select Custom to specify different values for the top, bottom, left, and right edges. |
| Spacing | Additional spacing (in points) to include between items in the interface controller. |

### Subclassing notes

Subclass `WKInterfaceController` when you have a storyboard scene that requires configuration at runtime or that handles user interactions. Typically, you define a custom subclass for each unique storyboard scene that your app manages. In your subclass, define outlets for any interface objects you need to configure and define action methods for responding to interactions with the elements of your storyboard scene.

Most custom interface controllers you use in your app require a custom interface controller subclass. Even glances need an interface controller to update the glance contents. The only storyboard scene that can’t use a custom interface controller is the scene associated with a static notification interface. When implementing an interface controller for your dynamic notification interface, subclass WKUserNotificationInterfaceController instead.

Override any methods of the class needed to configure your interface and get it ready to display. Most interface controllers override the init() and awake(withContext:) methods. Override any other methods that make sense based on your needs.

## Topics

### Creating the interface controller

init()

Returns an initialized interface controller object.

func awake(withContext: Any?)

Initializes the interface controller with the specified context data.

func setTitle(String?)

Sets the title of the interface.

### Responding to activation and appearance events

func willActivate()

Tells the interface controller that the system is about to activate its view.

func didDeactivate()

Tells the interface controller that its view is no longer active.

func didAppear()

Tells the interface controller that its view is now onscreen.

func willDisappear()

Tells the interface controller that its view is now offscreen.

### Implementing a navigation interface

func pushController(withName: String, context: Any?)

Pushes a new interface controller onto the screen.

func pop()

Pops the current interface controller from the screen.

func popToRootController()

Pops all interface controllers except the app’s initial interface controller.

### Presenting interface controllers modally

func presentController(withName: String, context: Any?)

Presents a single interface controller modally.

func presentController(withNames: [String], contexts: [Any]?)

Presents a page-based interface modally.

func presentController(withNamesAndContexts: [(name: String, context: AnyObject)])

Presents a page-based interface modally.

func presentAlert(withTitle: String?, message: String?, preferredStyle: WKAlertControllerStyle, actions: [WKAlertAction])

Presents an alert or action sheet over the current interface controller.

enum WKAlertControllerStyle

Constants indicating the styles for standard system alerts.

func dismiss()

Dismisses the current interface controller from the screen.

### Navigating a page-based interface

class func reloadRootPageControllers(withNames: [String], contexts: [Any]?, orientation: WKPageOrientation, pageIndex: Int)

Loads the specified interface controllers and rebuilds the app’s page-based interface for the given scrolling orientation.

enum WKPageOrientation

Scrolling orientations for page-based interfaces.

class func reloadRootControllers(withNamesAndContexts: [(name: String, context: AnyObject)])

Loads the specified interface controllers and rebuilds the app’s page-based interface.

func becomeCurrentPage()

Displays the interface controller in the page-based interface.

### Managing segue-based transitions

func contextForSegue(withIdentifier: String) -> Any?

Returns the context object to pass to the specified interface controller when a button is tapped.

func contextsForSegue(withIdentifier: String) -> [Any]?

Returns the context objects to pass to a page-based set of interface controllers when a button is tapped.

func contextForSegue(withIdentifier: String, in: WKInterfaceTable, rowIndex: Int) -> Any?

Returns the context object to pass to the specified interface controller when a row in a table is tapped.

func contextsForSegue(withIdentifier: String, in: WKInterfaceTable, rowIndex: Int) -> [Any]?

Returns the context objects to pass to a page-based set of interface controllers when a row in a table is tapped.

### Managing Scrolling

func scroll(to: WKInterfaceObject, at: WKInterfaceScrollPosition, animated: Bool)

Scrolls the specified object to the given position onscreen.

enum WKInterfaceScrollPosition

Onscreen scroll positions.

func interfaceDidScrollToTop()

Tells the interface controller that the user has performed a scroll-to-top gesture (for example, tapping the status bar) and that the scrolling animation has finished.

func interfaceOffsetDidScrollToTop()

Tells the interface controller that the user has scrolled to the top of the interface and that the scrolling animation has finished.

func interfaceOffsetDidScrollToBottom()

Tells the interface controller that the user has scrolled to the bottom of the interface and that the scrolling animation has finished.

var isTableScrollingHapticFeedbackEnabled: Bool

A Boolean value that determines whether haptic feedback coordinates with the appearance of new rows as the user scrolls through a table.

### Respecting safe areas and layout margins

var contentSafeAreaInsets: UIEdgeInsets

Insets that define the area where it’s safe to display content on the screen.

var systemMinimumLayoutMargins: NSDirectionalEdgeInsets

Leading and trailing insets that represent the minimum layout margins for text elements.

var contentFrame: CGRect

The frame rectangle used to display your app’s content.

### Animating changes to the interface

func animate(withDuration: TimeInterval, animations: () -> Void)

Animates changes to one or more interface objects over the specified duration.

### Handling text input

func presentTextInputController(withSuggestions: [String]?, allowedInputMode: WKTextInputMode, completion: ([Any]?) -> Void)

Displays a modal interface for gathering text input from the user.

func presentTextInputControllerWithSuggestions(forLanguage: ((String) -> [Any]?)?, allowedInputMode: WKTextInputMode, completion: ([Any]?) -> Void)

Displays a modal interface for gathering language-specific text input from the user.

func dismissTextInputController()

Dismisses the text input controller without returning any text.

enum WKTextInputMode

The input modes supported by the text input controller.

### Presenting video and audio interfaces

func presentMediaPlayerController(with: URL, options: [AnyHashable : Any]?, completion: (Bool, TimeInterval, (any Error)?) -> Void)

Displays a modal interface for playing the specified media file.

Media Player Options

Keys indicating media playback options.

func dismissMediaPlayerController()

Dismisses the media interface controller.

func presentAudioRecorderController(withOutputURL: URL, preset: WKAudioRecorderPreset, options: [AnyHashable : Any]?, completion: (Bool, (any Error)?) -> Void)

Display a standard interface for recording audio from the user’s Apple Watch.

enum WKAudioRecorderPreset

Constants indicating the quality of audio recordings.

Audio Recording Options

Options to specify when recording audio.

func dismissAudioRecorderController()

Dismisses the audio recording interface controller.

### Handling table-row selections

func table(WKInterfaceTable, didSelectRowAt: Int)

Called to let you know that the user selected a row in the table.

### Managing pickers

func pickerDidFocus(WKInterfacePicker)

Called to let you know that the specified picker is now receiving input from the Digital Crown.

func pickerDidResignFocus(WKInterfacePicker)

Called to let you know that the specified picker is no longer receiving input from the Digital Crown.

func pickerDidSettle(WKInterfacePicker)

Called to let you know when the user settles on a value in a picker.

### Getting the crown sequencer

var crownSequencer: WKCrownSequencer

The object to use when directly tracking crown events.

### Coordinating Handoff activity

func update(NSUserActivity)

Registers the current user activity with the system.

func invalidateUserActivity()

Invalidates the most recent user activity.

### Adding PassKit passes

func presentAddPassesController(withPasses: [PKPass], completion: () -> Void)

Displays a modal interface for presenting passes to the user.

func dismissAddPassesController()

Dismisses the pass interface controller

### Managing Notifications

let WKAccessibilityVoiceOverStatusChanged: String

Tells the interface controller that the VoiceOver status has changed.

### Deprecated symbols

Text Response Key

Keys for retrieving text response information.

func addMenuItem(withImageNamed: String, title: String, action: Selector)

Adds an action to the context menu using an existing image resource in your Watch app bundle.

Deprecated

func addMenuItem(with: WKMenuItemIcon, title: String, action: Selector)

Adds an action to the context menu using a system-provided icon.

Deprecated

func addMenuItem(with: UIImage, title: String, action: Selector)

Adds an action to the context menu by using an image provided by your WatchKit extension.

Deprecated

func beginGlanceUpdates()

Tells the system that you are about to start a potentially lengthy update task for your glance.

Deprecated

func clearAllMenuItems()

Removes all programmatically added actions from the context menu.

Deprecated

func endGlanceUpdates()

Tells the system that you finished updating your glance content.

Deprecated

func handleUserActivity([AnyHashable : Any]?)

Responds to Handoff–related activity.

Deprecated

func presentController([(name: String, context: AnyObject)])

Presents a page-based interface modally.

Deprecated

class func reloadRootControllers(withNames: [String], contexts: [Any]?)

Loads the specified interface controllers and rebuilds the app’s page-based interface.

Deprecated

func updateUserActivity(String, userInfo: [AnyHashable : Any]?, webpageURL: URL?)

Registers the current user activity with the system.

Deprecated

enum WKMenuItemIcon

Template images that you can use for menus.

Deprecated

## Relationships

### Inherits From

- NSObject

### Inherited By

- WKUserNotificationInterfaceController

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSObjectProtocol
- Sendable

## See Also

### User interface basics

Building watchOS app Interfaces Using the Storyboard

Create the user interface for your watchOS app by nesting stacks.

class WKInterfaceObject

An object that provides information that is common to all interface objects in your watchOS app.

class WKAlertAction

An object that encapsulates information about a button displayed in an alert or action sheet.

class WKAccessibilityImageRegion

An object that defines a portion of an image that you want to call out separately to an assistive app.

func WKAccessibilityIsVoiceOverRunning() -> Bool

Returns a Boolean value indicating whether VoiceOver is running.

func WKAccessibilityIsReduceMotionEnabled() -> Bool

Returns a Boolean value indicating whether reduced motion is enabled.

