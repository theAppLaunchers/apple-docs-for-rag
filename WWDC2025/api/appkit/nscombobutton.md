*   [AppKit](/documentation/appkit)
*   NSComboButton

Class

# NSComboButton

A button with a pull-down menu and a default action.

macOS 13.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift

```swift
@[`MainActor`](/documentation/Swift/MainActor)
class NSComboButton
```

```
```
```
```
```
```
```

## [Overview](/documentation/AppKit/NSComboButton#overview)

An [`NSComboButton`](/documentation/appkit/nscombobutton) object is a button that displays a title string, image, and an optional control for displaying a menu. Use this control in places where you want to offer a button with a default action and one or more alternative actions. Clicking the title or image executes the default action you provide, and clicking the menu control displays a menu for selecting a different action. If you configure the button to hide the menu control, a long-press gesture displays the menu.

After you create a combo button programmatically or in Interface Builder, choose the button [`style`](/documentation/appkit/nscombobutton/style-swift.property) you want and add a title or image for your content. A combo button has a default action, which you specify at creation time. You can also change that action later using the inherited [`target`](/documentation/appkit/nscontrol/target) and [`action`](/documentation/appkit/nscontrol/action) properties. To specify one or more alternative actions, configure a menu with those actions and assign it to the button’s [`menu`](/documentation/appkit/nscombobutton/menu) property.

This control doesn’t use an [`NSCell`](/documentation/appkit/nscell) object for its underlying implementation. It also doesn’t support the addition of a contextual menu.

## [Topics](/documentation/AppKit/NSComboButton#topics)

### [Creating a Combo Button](/documentation/AppKit/NSComboButton#Creating-a-Combo-Button)

[`convenience init(title: String, image: NSImage, menu: NSMenu?, target: Any?, action: Selector?)`](/documentation/appkit/nscombobutton/init\(title:image:menu:target:action:\))

Creates a combo button that displays both a title and image.

[`convenience init(title: String, menu: NSMenu?, target: Any?, action: Selector?)`](/documentation/appkit/nscombobutton/init\(title:menu:target:action:\))

Creates a combo button that displays a title.

[`convenience init(image: NSImage, menu: NSMenu?, target: Any?, action: Selector?)`](/documentation/appkit/nscombobutton/init\(image:menu:target:action:\))

Creates a combo button that displays an image.

### [Configuring the Button Appearance](/documentation/AppKit/NSComboButton#Configuring-the-Button-Appearance)

```swift
```swift
```swift
```swift
var style: NSComboButton.Style
```
```

The appearance setting that determines how the button presents its menu .
```
```swift
```swift
```swift
enum Style
```
```

Constants that indicate how a combo button presents its menu.
```
```swift
```swift
```swift
var title: String
```
```

The localized string that the button displays.
```
```swift
```swift
```swift
var image: NSImage?
```
```

The image that the button displays.
```
```swift
```swift
```swift
var imageScaling: NSImageScaling
```
```

The scaling behavior to apply to the button’s image.
```
```

### [Specifying the Alternative Actions](/documentation/AppKit/NSComboButton#Specifying-the-Alternative-Actions)

```swift
```swift
```swift
```swift
var menu: NSMenu
```
```

The menu that contains the button’s alternate actions.
```
```

## [Relationships](/documentation/AppKit/NSComboButton#relationships)

### [Inherits From](/documentation/AppKit/NSComboButton#inherits-from)

*   [`NSControl`](/documentation/appkit/nscontrol)

### [Conforms To](/documentation/AppKit/NSComboButton#conforms-to)

*   [`CVarArg`](/documentation/Swift/CVarArg)
*   [`CustomDebugStringConvertible`](/documentation/Swift/CustomDebugStringConvertible)
*   [`CustomStringConvertible`](/documentation/Swift/CustomStringConvertible)
*   [`Equatable`](/documentation/Swift/Equatable)
*   [`Hashable`](/documentation/Swift/Hashable)
*   [`NSAccessibilityElementProtocol`](/documentation/appkit/nsaccessibilityelementprotocol)
*   [`NSAccessibilityProtocol`](/documentation/appkit/nsaccessibilityprotocol)
*   [`NSAnimatablePropertyContainer`](/documentation/appkit/nsanimatablepropertycontainer)
*   [`NSAppearanceCustomization`](/documentation/appkit/nsappearancecustomization)
*   [`NSCoding`](/documentation/Foundation/NSCoding)
*   [`NSDraggingDestination`](/documentation/appkit/nsdraggingdestination)
*   [`NSObjectProtocol`](/documentation/ObjectiveC/NSObjectProtocol)
*   [`NSStandardKeyBindingResponding`](/documentation/appkit/nsstandardkeybindingresponding)
*   [`NSTouchBarProvider`](/documentation/appkit/nstouchbarprovider)
*   [`NSUserActivityRestoring`](/documentation/appkit/nsuseractivityrestoring)
*   [`NSUserInterfaceItemIdentification`](/documentation/appkit/nsuserinterfaceitemidentification)
*   [`Sendable`](/documentation/Swift/Sendable)
*   [`SendableMetatype`](/documentation/Swift/SendableMetatype)

## [See Also](/documentation/AppKit/NSComboButton#see-also)

### [Controls](/documentation/AppKit/NSComboButton#Controls)

[

Responding to control-based events using target-action](/documentation/UIKit/responding-to-control-based-events-using-target-action)

Handle user input by connecting buttons, sliders, and other controls to your app’s code using the target-action design pattern.

```swift
```swift
```swift
class NSButton
```
```

A control that defines an area on the screen that a user clicks to trigger an action.
```
```swift
```swift
```swift
class NSColorWell
```
```

A control that displays a color value and lets the user change that color value.
```

[

API Reference

Combo Box](/documentation/appkit/combo-box)

Display a list of values in a pop-up menu that lets the user select a value or type in a custom value.

[

API Reference

Date Picker](/documentation/appkit/date-picker)

Display a calendar date and provide controls for editing the date value.

```swift
```swift
```swift
class NSImageView
```
```

A display of image data in a frame.
```
```swift
```swift
```swift
class NSLevelIndicator
```
```

A visual representation of a level or quantity, using discrete values.
```

[

API Reference

Path Control](/documentation/appkit/path-control)

A display of a file system path or virtual path information.

```swift
```swift
```swift
class NSPopUpButton
```
```

A control for selecting an item from a list.
```
```swift
```swift
```swift
class NSProgressIndicator
```
```

An interface that provides visual feedback to the user about the status of an ongoing task.
```
```swift
```swift
```swift
class NSRuleEditor
```
```

An interface for configuring a rule-based list of options.
```
```swift
```swift
```swift
class NSPredicateEditor
```
```

A defined set of rules that allows the editing of predicate objects.
```

[

API Reference

Search Field](/documentation/appkit/search-field)

Provide a text field that is optimized for text-based search interfaces.

```swift
```swift
```swift
class NSSegmentedControl
```
```

Display one or more buttons in a single horizontal group.
```

[

API Reference

Slider](/documentation/appkit/slider)

Display a range of values from which the user selects a single value.