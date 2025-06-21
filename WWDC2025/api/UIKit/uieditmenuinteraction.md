*   [UIKit](/documentation/uikit)
*   UIEditMenuInteraction

Class

# UIEditMenuInteraction

An interaction that provides edit operations using a menu.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+visionOS 1.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift

```swift
@[`MainActor`](/documentation/Swift/MainActor)
class UIEditMenuInteraction
```

```
```
```
```
```
```
```

## [Mentioned in](/documentation/UIKit/UIEditMenuInteraction#mentions)

[

Building a desktop-class iPad app](/documentation/uikit/building-a-desktop-class-ipad-app)

## [Overview](/documentation/UIKit/UIEditMenuInteraction#overview)

Edit menu interactions provide edit actions — such as cut, copy, and paste — for the content a view displays. The presentation style the interaction uses to display the actions conforms to the input method of the interaction. For touch interactions, the actions display in an editing menu. When responding to a secondary click on devices with pointer-based input, the actions display in a context menu.

Standard UIKit classes, such as [`UITextView`](/documentation/uikit/uitextview) and [`UITextField`](/documentation/uikit/uitextfield), are preconfigured to use edit menu interactions.

To add an edit menu interaction to a generic view:

1.  Create an edit menu interaction object, and pass an optional delegate into the default initializer.
    
2.  Call the [`addInteraction(_:)`](/documentation/uikit/uiview/addinteraction\(_:\)) method on your view to add the interaction.
    
3.  Create a gesture recognizer to trigger the interaction and add it to the view.
    

The following example creates an edit menu interaction triggered by a long press.

```swift

```swift
override func viewDidLoad() {
    super.viewDidLoad()
    // Add the edit menu interaction.
    editMenuInteraction = UIEditMenuInteraction(delegate: self)
    interactionView.addInteraction(editMenuInteraction!)
    // Create the gesture recognizer.
    let longPress = UILongPressGestureRecognizer(target: self, action: #selector(didLongPress(_:)))
    longPress.allowedTouchTypes = [UITouch.TouchType.direct.rawValue as NSNumber]
    interactionView.addGestureRecognizer(longPress)
}
@objc func didLongPress(_ recognizer: UIGestureRecognizer) {
    let location = recognizer.location(in: self.view)
    let configuration = UIEditMenuConfiguration(identifier: nil, sourcePoint: location)
    if let interaction = editMenuInteraction {
        // Present the edit menu interaction.
        interaction.presentEditMenu(with: configuration)
    }
}
```

```

By default, an edit menu interaction generates a menu that includes commands for the standard edit actions your view implements. For more information on these actions, see [`UIResponderStandardEditActions`](/documentation/uikit/uiresponderstandardeditactions). You can use the interaction’s delegate to add additional items to the menu and set the target rectangle to display around using methods in the [`UIEditMenuInteractionDelegate`](/documentation/uikit/uieditmenuinteractiondelegate) protocol. For text views, you can specify the items the menu displays for specific text ranges using methods from the [`UITextViewDelegate`](/documentation/uikit/uitextviewdelegate), [`UITextFieldDelegate`](/documentation/uikit/uitextfielddelegate), or [`UITextInput`](/documentation/uikit/uitextinput) protocols.

Related Sessions from WWDC22

Session 10071: [Adopt desktop-class editing interactions](https://developer.apple.com/wwdc22/10071)

## [Topics](/documentation/UIKit/UIEditMenuInteraction#topics)

### [Creating an edit menu interaction](/documentation/UIKit/UIEditMenuInteraction#Creating-an-edit-menu-interaction)

[`init(delegate: (any UIEditMenuInteractionDelegate)?)`](/documentation/uikit/uieditmenuinteraction/init\(delegate:\))

Initializes an edit menu interaction object with the delegate object you specify.

### [Managing edit menu interactions](/documentation/UIKit/UIEditMenuInteraction#Managing-edit-menu-interactions)

```swift
```swift
```swift
```swift
var delegate: (any UIEditMenuInteractionDelegate)?
```
```

An object that customizes presentation of the menu and actions to display for an edit menu interaction.
```
```swift
```swift
```swift
func presentEditMenu(with: UIEditMenuConfiguration)
```
```

Presents an edit menu using the object you provide for configuration.
```
```swift
```swift
```swift
func reloadVisibleMenu()
```
```

Updates the actions an edit menu displays.
```
```swift
```swift
```swift
func updateVisibleMenuPosition(animated: Bool)
```
```

Updates the position of the currently visible menu with an option to animate the action.
```
```swift
```swift
```swift
func dismissMenu()
```
```

Dismiss the edit menu if present.
```
```swift
```swift
```swift
func location(in: UIView?) -> CGPoint
```
```

Returns the location of the user interaction in the specified view’s coordinate system.
```
```

## [Relationships](/documentation/UIKit/UIEditMenuInteraction#relationships)

### [Inherits From](/documentation/UIKit/UIEditMenuInteraction#inherits-from)

*   [`NSObject`](/documentation/ObjectiveC/NSObject-swift.class)

### [Conforms To](/documentation/UIKit/UIEditMenuInteraction#conforms-to)

*   [`CVarArg`](/documentation/Swift/CVarArg)
*   [`CustomDebugStringConvertible`](/documentation/Swift/CustomDebugStringConvertible)
*   [`CustomStringConvertible`](/documentation/Swift/CustomStringConvertible)
*   [`Equatable`](/documentation/Swift/Equatable)
*   [`Hashable`](/documentation/Swift/Hashable)
*   [`NSObjectProtocol`](/documentation/ObjectiveC/NSObjectProtocol)
*   [`Sendable`](/documentation/Swift/Sendable)
*   [`UIInteraction`](/documentation/uikit/uiinteraction)

## [See Also](/documentation/UIKit/UIEditMenuInteraction#see-also)

### [Related Documentation](/documentation/UIKit/UIEditMenuInteraction#Related-Documentation)

[

Building a desktop-class iPad app](/documentation/uikit/building-a-desktop-class-ipad-app)

Optimize your iPad app’s user experience by adopting desktop-class enhancements for multitasking with Stage Manager, document interactions, text editing, search, and more.

### [Edit menus](/documentation/UIKit/UIEditMenuInteraction#Edit-menus)

```swift
```swift
```swift
```swift
protocol UIEditMenuInteractionDelegate
```
```

The methods for customizing the menu the interaction displays.
```
```swift
```swift
```swift
class UIEditMenuConfiguration
```
```

An object containing the configuration details for the menu your app presents in response to an edit menu interaction.
```
```swift
```swift
```swift
protocol UIResponderStandardEditActions
```
```

A set of standard methods that apps can adopt to support editing.
```
```