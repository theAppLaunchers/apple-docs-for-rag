

- WatchKit
-  WKInterfaceLabel 

Class

# WKInterfaceLabel

An interface element that displays static text.

watchOS 2.0+

``` source
class WKInterfaceLabel
```

## Mentioned in 

Connecting Your User Interface to Your Code

## Overview

Use WKInterfaceLabel to manipulate the contents of a label at runtime, such as setting a new text string. The string you specify can use the default styling you specified at design time, or you can use an attributed string to add custom styling to the text.

Do not subclass or create instances of this class yourself. Instead, define outlets in your interface controller class and connect them to the corresponding objects in your storyboard file. For example, to refer to a label object in your interface, define a property with the following syntax in your interface controller class:

- Swift
- Objective-C

```
@IBOutlet weak var myLabel: WKInterfaceLabel!
```

```
@property (weak, nonatomic) IBOutlet WKInterfaceLabel* myLabel;
```

During the initialization of your interface controller, WatchKit creates any needed label objects and assigns them to their connected outlets. At that point, you can use those objects to make changes to the onscreen text.

Label objects apply the font and style information specified in your storyboard. You can specify a different set of style attributes by calling the setAttributedText(_:) method and providing an appropriately formatted attributed string object. When specifying text with an NSString object, the only other change you can make is to the text color.

### Interface Builder Configuration Options

Xcode lets you configure information about your label interface object in your storyboard file. The following table lists the attributes you can configure and their meaning.

| Attribute | Description |
|----|----|
| Text | The initial text to be displayed. You can change this value programmatically using the setText(_:) or setAttributedText(_:) method. |
| Text Color | The default color of the text. You can also set this value programmatically using the setTextColor(_:) method. |
| Font | The font information to be applied to the text. You can specify one of the predefined styles or provide custom style information. For custom fonts, you must include the font in your WatchKit app bundle. You can also apply font information when using the setAttributedText(_:) method. |
| Min Scale | The amount by which the font may be scaled to accommodate text. Values must be `1.0` or less. Specifying a value of `0` causes WatchKit to use the default scaling behavior, which allows scaling to `0.8` of the original font size. |
| Baseline | The technique for adjusting the position of the label’s text. When centering text vertically, you can center the text relative to the baseline or to the center of the label’s bounding box. |
| Alignment | The alignment of the text within its bounding rectangle. Use this attribute to align text when the width of the label is greater than the width of the text itself. |
| Lines | The maximum number of lines to allow for the label text. Text that does not fit on the specified number of lines is truncated. |

## Topics

### Setting the Label Text

func setText(String?)

Sets the label text to the specified string.

func setTextColor(UIColor?)

Sets the color to apply to plain text strings.

func setAttributedText(NSAttributedString?)

Sets the label text to the specified attributed string.

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

class WKInterfaceSwitch

An interface element that toggles between an On and Off state.

class WKInterfaceSlider

An interface element that lets users select a single floating-point value from a range of values.

class WKInterfaceActivityRing

A view that displays data from a HealthKit activity summary object.

class WKInterfaceMap

An interface element that displays a noninteractive map for the location you specify.

