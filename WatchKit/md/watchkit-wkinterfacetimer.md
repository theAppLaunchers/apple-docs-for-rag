

- WatchKit
-  WKInterfaceTimer 

Class

# WKInterfaceTimer

A label that displays a countdown or count-up timer.

watchOS 2.0+

``` source
class WKInterfaceTimer
```

## Overview

Use a timer object to configure the amount of time and the appearance of the timer text. When you start the timer, WatchKit updates the displayed text automatically on the user’s Apple Watch without further interactions from your extension. To know when the timer reaches 0, configure a Timer object with the same target date you used to set up the timer.

Do not subclass or create instances of this class yourself. Instead, define outlets in your interface controller class and connect them to the corresponding objects in your storyboard file. For example, to refer to a timer object in your interface, define a property with the following syntax in your interface controller class:

- Swift
- Objective-C

```
@IBOutlet weak var myTimer: WKInterfaceTimer!
```

```
@property (weak, nonatomic) IBOutlet WKInterfaceTimer* myTimer;
```

During the initialization of your interface controller, WatchKit creates any needed timer objects and assigns them to their connected outlets. At that point, you can use those objects to reconfigure the corresponding timers.

Important

This class provides methods for configuring interface objects at initialization time or while an interface controller is active on the user’s Apple Watch. WatchKit coalesces the data from all setter method calls made during the same run loop iteration and transmits it to the device at the end of the run loop. If you set an attribute to different values in the same run loop iteration, only the last value is transmitted. If you set an attribute to the same value in the same run loop iteration, WatchKit generates a log message so that you can track down the duplicate change.

### Interface Builder Configuration Options

Xcode lets you configure information about your timer interface object in your storyboard file. The following table lists the attributes you can configure and their meaning.

| Attribute | Description |
|----|----|
| Format | The format of the timer string. Select different options to update the appearance of the timer label in your storyboard scene. |
| Enabled | A checkbox indicating whether the timer starts running as soon as your interface is initialized. |
| Units | The units to be displayed in the label. Enabling checkboxes in this section causes the timer to display the corresponding units that are in range of the time. In other words, a timer with 2 minutes remaining displays minutes and seconds only; it does not display hours, days, or any larger units. |
| Preview Secs | The initial number of seconds for the timer. You can change this value programmatically using the setDate(_:) method. |

A date object is a custom label whose text you cannot set directly. However, you can customize the appearance of the date object as you would for a label using the Attributes inspector in Xcode. For information about the label attributes you can configure, see WKInterfaceLabel.

## Topics

### Configuring the Timer Attributes

func setDate(Date)

Changes the start time for the timer.

func setTextColor(UIColor?)

Sets the color of the timer’s text.

### Starting and Stopping the Timer

func start()

Begins updates to the timer’s display.

func stop()

Stops updates to the timer’s display.

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

