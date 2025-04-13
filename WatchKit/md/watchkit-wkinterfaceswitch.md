

- WatchKit
-  WKInterfaceSwitch 

Class

# WKInterfaceSwitch

An interface element that toggles between an On and Off state.

watchOS 2.0+

``` source
class WKInterfaceSwitch
```

## Overview

Switches are commonly used to indicate whether a feature is enabled or disabled. You set the initial value of the switch in your storyboard file, but you can modify that value at runtime using the methods of this class.

Do not subclass or create instances of this class yourself. Instead, define outlets in your interface controller class and connect them to the corresponding objects in your storyboard file. For example, to refer to a switch object in your interface, define a property with the following syntax in your interface controller class:

- Swift
- Objective-C

```
@IBOutlet weak var mySwitch: WKInterfaceSwitch!
```

```
@property (weak, nonatomic) IBOutlet WKInterfaceSwitch* mySwitch;
```

During the initialization of your interface controller, WatchKit creates a new instance of this class and assigns it to your outlet. At that point, you can use the object in your outlet to make changes to the onscreen switch.

When the user changes the value of a switch, WatchKit delivers the new value to the slider’s action method. The format of a switch’s action method is as follows:

- Swift
- Objective-C

```
@IBAction func switchAction(value: Bool)
```

```
- (IBAction)switchAction:(BOOL)on
```

Declare a method of this form in the interface controller class used to manage the switch. You can change the method name to anything you like. When configuring the switch in Xcode, connect its selector to your custom action method.

### Interface Builder Configuration Options

Xcode lets you configure information about switches in your storyboard file. The following table lists the attributes you can configure and their meaning.

| Attribute | Description |
|----|----|
| State | The initial state of the switch. The switch can be off or on. You can modify the state of the switch programmatically at runtime using the setOn(_:) method. |
| Tint | The color of the switch when it is in the on state. |
| Enabled | A checkbox indicating whether the switch is enabled. An enabled switch calls its action method when the user changes the state of the switch. You can enable or disable a switch programmatically using the setEnabled(_:) method. |
| Title | The string to be displayed next to the switch. If specified, the title string is displayed next to the switch. |
| Color | The text color for the switch’s title string. You can also set the switch color using the setColor(_:) method. |
| Font | The font information to be applied to the title string. You can specify one of the predefined styles or provide custom style information. |

## Topics

### Setting the Switch’s Title

func setTitle(String?)

Sets the switch title to the specified string.

func setAttributedTitle(NSAttributedString?)

Sets the switch title to the specified attributed string.

### Configuring the Switch

func setOn(Bool)

Sets the state of the switch to the specified value.

func setColor(UIColor?)

Changes the tint color of the switch when it is on.

### Enabling the Switch

func setEnabled(Bool)

Enables or disables the switch.

## Relationships

### Inherits From

- WKInterfaceObject

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSObjectProtocol

## See Also

### Controls

class WKInterfaceLabel

An interface element that displays static text.

class WKInterfaceDate

A label that displays the current date or time.

class WKInterfaceTimer

A label that displays a countdown or count-up timer.

class WKInterfaceButton

A button in the user interface of your watchOS app.

class WKInterfaceAuthorizationAppleIDButton

A button that you can use to trigger a Sign in with Apple request.

class WKInterfacePaymentButton

A button that you can use to trigger payments through Apple Pay.

class WKInterfaceTextField

An interface element that displays an editable text area.

class WKInterfaceSlider

An interface element that lets users select a single floating-point value from a range of values.

class WKInterfaceActivityRing

A view that displays data from a HealthKit activity summary object.

class WKInterfaceMap

An interface element that displays a noninteractive map for the location you specify.

