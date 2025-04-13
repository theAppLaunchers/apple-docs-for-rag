

- WatchKit
-  WKLongPressGestureRecognizer 

Class

# WKLongPressGestureRecognizer

A gesture recognizer that interprets a touch event that occurs in the same relative area for an extended period of time.

watchOS 3.0+

``` source
class WKLongPressGestureRecognizer
```

## Overview

A long-press gesture is essentially a tap where the user’s finger remains on the screen for a minimum amount of time, which is configurable. You can configure the amount of time required for the long-press to be recognized and the maximum distance those touches are allowed to move before being disallowed.

You do not create instances of this class programmatically. Instead, add a long-press gesture recognizer to your Watch app’s storyboard file, dropping it onto a specific interface object. Touches occurring within the bounds of that interface object are tracked by the gesture recognizer and reported to an action method you define on the parent interface controller. For information on defining your action method and connecting it to your gesture recognizer, see WKGestureRecognizer.

### State Changes for a Long-Press Gesture

A long-press gesture recognizer tracks touch events continuously, and therefore has many potential state changes. A long-press gesture transitions to the Began state when the touch event is first detected. After that, the gesture recognizer may transition to the Changed state, the Ended, state, the Failed state, or the Cancelled state. The two most common state transition sequences are as follows:

- Possible → Began → \[Changed…\] → Ended

- Possible → Began → \[Changed…\] → Failed

The Changed state is optional and may occur multiple times before the Ended, Failed, or Cancelled state is reached. The gesture recognizer calls its action method at each state transition. For more information on implementing continuous gesture recognizers, see WKGestureRecognizer.

### Interface Builder Attributes

Xcode lets you configure information about your gesture recognizer in your storyboard file. The following table lists the attributes you can configure in your storyboard and their meaning.

| Attribute | Description |
|----|----|
| Min Duration | The minimum time (in seconds) that the user’s finger must touch the screen before the gesture can be recognized. You can set this value programmatically using the minimumPressDuration property. |
| Taps | The number of long-press taps that must occur for the gesture to be recognized. Each tap must touch the screen for the minimum duration. You can set this value programmatically using the numberOfTapsRequired property. |
| Movement | The amount of movement (in points) allowed for each touch event. Recognition of the gesture fails if any of the touch events moves by the specified amount or more. You can set this value programmatically using the allowableMovement property. |

The WKGestureRecognizer parent class also defines attributes that you can configure for your gesture recognizer. For information about those attributes, see WKGestureRecognizer.

## Topics

### Configuring the Gesture Recognizer

var minimumPressDuration: CFTimeInterval

The minimum amount of time (in seconds) that the user’s fingers must be touching the interface object.

var numberOfTapsRequired: Int

The number of taps on the interface object that are required for the gesture to be recognized.

var allowableMovement: CGFloat

The maximum movement of the finger on the interface object that allows the gesture to be recognized.

## Relationships

### Inherits From

- WKGestureRecognizer

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSObjectProtocol

## See Also

### Event handling

class WKCrownSequencer

An object that reports the current state of the digital crown, including its rotational speed when it is in motion.

protocol WKCrownDelegate

A collection of methods you can implement to track the user’s interaction with the digital crown, receiving notifications when the user rotates the crown or when rotation stops.

class WKGestureRecognizer

The base class for all other gesture recognizer classes.

class WKPanGestureRecognizer

A gesture recognizer that interprets a touch event that moves around the screen.

class WKSwipeGestureRecognizer

A gesture recognizer that interprets swiping gestures in one or more directions.

class WKTapGestureRecognizer

A gesture recognizer that interprets a touch event occurring and ending in approximately the same area on the screen.

