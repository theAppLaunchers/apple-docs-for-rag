

- AppKit
-  NSAlignmentFeedbackFilter 

Class

# NSAlignmentFeedbackFilter

An object that can filter the movement of an object and provides haptic feedback when alignment occurs.

macOS 10.11+

``` source
class NSAlignmentFeedbackFilter
```

## Overview

With a Force Touch trackpad, apps can produce tactile feedback to complement user actions. If your app implements alignment features, you can use the NSAlignmentFeedbackFilter class to filter object movements and provide haptic feedback to the user at appropriate times. As the user drags objects into alignment with a guide or another object, the user actually feels a physical bump as the object snaps into place.

### Implementing Alignment Feedback

To implement alignment feedback in your custom alignment controller class, set up the class to receive events for tracking the movement of an object. These can be events matching the inputEventMask value of an `NSAlignmentFeedbackFilter` object, or events from a gesture recognizer (NSGestureRecognizer). For each event received:

1.  Create an instance of an `NSAlignmentFeedbackFilter` object. For example:

- Swift
- Objective-C

```
let self.feedbackFilter = NSAlignmentFeedbackFilter()
```

```
self.feedbackFilter = [NSAlignmentFeedbackFilter new];
```

2.  Inform the alignment feedback filter object about the event. To do this, call one of the following methods:

- update(with:)

- update(withPanRecognizer:)

3.  Store the location of the object before it moves in response to the event. This is considered the *previous* location of the object.

4.  Move the object to its new location in response to the event. This is the location where the object will reside if no alignment occurs.

5.  Store the new location of the object. This is considered the *default* location of the object.

6.  Determine where the object will move to be aligned. This is considered the *aligned* location of the object.

7.  Request a feedback token based on the previous location, default location, and aligned location. To do this, call one of the following methods:

- alignmentFeedbackTokenForMovement(in:previousPoint:alignedPoint:defaultPoint:) - If the object will be moved both horizontally and vertically to become aligned.

- alignmentFeedbackTokenForHorizontalMovement(in:previousX:alignedX:defaultX:) - If the object will be moved horizontally only to become aligned.

- alignmentFeedbackTokenForVerticalMovement(in:previousY:alignedY:defaultY:) - If the object will be moved vertically only to become aligned.

8.  If a feedback token is successfully prepared, call performFeedback(_:performanceTime:) to perform the haptic feedback. Then, move the object to the aligned location.

If a value of `null` is returned, rather than a feedback token, then the system has determined that alignment and feedback are not appropriate. Perhaps the cursor is moving too fast or the distance to the aligned location is not significant enough to produce a visual snap. Move the object to its default location.

## Topics

### Determining Event Types for the Filter

class var inputEventMask: NSEvent.EventTypeMask

Retrieves the event types the filter accepts.

### Informing the Filter About Events

func update(with: NSEvent)

Informs the feedback filter about a new event.

func update(withPanRecognizer: NSPanGestureRecognizer)

Informs the feedback filter about a new pan (drag) gesture recognizer event.

### Preparing Haptic Feedback for Alignment

func alignmentFeedbackTokenForMovement(in: NSView?, previousPoint: NSPoint, alignedPoint: NSPoint, defaultPoint: NSPoint) -> (any NSAlignmentFeedbackToken)?

Requests a feedback token for the alignment of an object requiring horizontal and vertical movement.

func alignmentFeedbackTokenForHorizontalMovement(in: NSView?, previousX: CGFloat, alignedX: CGFloat, defaultX: CGFloat) -> (any NSAlignmentFeedbackToken)?

Requests a feedback token for the alignment of an object requiring horizontal movement only.

func alignmentFeedbackTokenForVerticalMovement(in: NSView?, previousY: CGFloat, alignedY: CGFloat, defaultY: CGFloat) -> (any NSAlignmentFeedbackToken)?

Requests a feedback token for the alignment of an object requiring vertical movement only.

### Providing Feedback to the User

func performFeedback([any NSAlignmentFeedbackToken], performanceTime: NSHapticFeedbackManager.PerformanceTime)

Performs the haptic feedback described by one or more alignment feedback tokens.

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

## See Also

### Haptics

class NSHapticFeedbackManager

An object that provides access to the haptic feedback management attributes on a system with a Force Touch trackpad.

protocol NSHapticFeedbackPerformer

A set of methods and constants that a haptic feedback performer implements.

protocol NSAlignmentFeedbackToken

