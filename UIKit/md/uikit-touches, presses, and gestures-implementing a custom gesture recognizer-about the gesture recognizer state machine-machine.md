

- UIKit
- Touches, presses, and gestures
- Implementing a custom gesture recognizer
-  About the Gesture Recognizer State Machine 

Article

# About the Gesture Recognizer State Machine

Learn about the states and transitions of the state machine that underlies gesture recognizers.

## Overview

Gesture recognizers are driven by a state machine, which UIKit uses to ensure the proper handling of events. The state machine determines several important behaviors:

- Whether a continuous gesture recognizer is allowed to enter the UIGestureRecognizer.State.began state

- Whether a discrete gesture recognizer is allowed to enter the UIGestureRecognizer.State.ended state

- When calls to attached action handlers occur

When implementing a custom gesture recognizer, you must update its state machine at appropriate times. A gesture recognizer always starts in the UIGestureRecognizer.State.possible state, which indicates that it is ready to start processing events. From that state, discrete and continuous gesture recognizers follow different paths until they reach the UIGestureRecognizer.State.ended, UIGestureRecognizer.State.failed, or UIGestureRecognizer.State.cancelled state. A gesture recognizer remains in one of those final states until the current event sequence ends, at which point UIKit resets the gesture recognizer and returns it to the UIGestureRecognizer.State.possible state.

### Managing State Transitions for a Discrete Gesture Recognizer

When implementing a discrete gesture recognizer, you change the state property to one of two possible values: UIGestureRecognizer.State.ended or UIGestureRecognizer.State.failed. The following image shows the state diagram for these transitions. When incoming events successfully match your gesture, change the state to UIGestureRecognizer.State.ended. When events do not match your intended gesture, change the state to UIGestureRecognizer.State.failed as soon as you detect the failure.

When your gesture recognizer transitions to the UIGestureRecognizer.State.ended state, UIKit calls the action methods of any associated target objects. UIKit does not call any action methods when the gesture recognizer transitions to the UIGestureRecognizer.State.failed state.

For an example of how to implement a discrete gesture recognizer, see Implementing a Discrete Gesture Recognizer.

### Managing State Transitions for a Continuous Gesture Recognizer

The following image shows the state diagram for a continuous gesture recognizer. The state transitions you make can be broken down into three general phases:

1.  The initial event sequence moves the gesture recognizer to the UIGestureRecognizer.State.began or UIGestureRecognizer.State.failed state.

2.  Subsequent events move the gesture recognizer to the UIGestureRecognizer.State.changed or UIGestureRecognizer.State.cancelled state.

3.  A final event moves the gesture recognizer to the UIGestureRecognizer.State.ended state.

When your gesture recognizer is in the UIGestureRecognizer.State.possible state, if the initial event sequence does not match your gesture, move your gesture recognizer to the UIGestureRecognizer.State.failed state immediately. UIKit normally permits only one gesture recognizer at a time to notify its client. Moving your custom gesture recognizer to the failed state gives other gesture recognizers an opportunity to handle their gestures.

If the initial event sequence matches your gesture, move your gesture recognizer to the UIGestureRecognizer.State.began state. For any subsequent events, repeatedly move your gesture recognizer to the UIGestureRecognizer.State.changed state to indicate that the event information has changed. (Always set the gesture recognizer’s state property to UIGestureRecognizer.State.changed for each new event, even if the property is already set to that value. Setting that property triggers calls to the associated action methods.) When an event indicates the successful completion of your gesture, change the state to UIGestureRecognizer.State.ended. However, if an event indicates the unsuccessful completion of your gesture, change the state to UIGestureRecognizer.State.cancelled.

When your gesture recognizer transitions to the UIGestureRecognizer.State.began, UIGestureRecognizer.State.changed, or UIGestureRecognizer.State.ended states, UIKit calls the action methods of any associated targets. UIKit does not call any action methods when your gesture recognizer transitions to other states.

For an example of how to implement a continuous gesture recognizer, see Implementing a Continuous Gesture Recognizer.

### Handling Cancellation

Cancellation of a gesture occurs automatically when the current event sequence is interrupted by a system event, such as an incoming phone call. You can also cancel a gesture programmatically based on event information or on conditions in your app. Cancellation prevents the gesture recognizer from performing tasks that the user didn’t intend.

When the system cancels a gesture, UIKit calls the touchesCancelled(_:with:) or pressesCancelled(_:with:) method of your gesture recognizer. When that happens, move your gesture recognizer to the UIGestureRecognizer.State.cancelled state immediately. When you move your gesture recognizer to the UIGestureRecognizer.State.cancelled state, UIKit calls the gesture recognizer’s action methods one final time before resetting it.

### Resetting the Gesture Recognizer State Machine

Implement the reset() method and use it to return your gesture recognizer to its initial configuration. For example, use this method to return your gesture recognizer’s custom properties to their starting values. Before delivering events in a new event sequence, UIKit calls the reset() method of every gesture recognizer that received touches or is in the UIGestureRecognizer.State.failed, UIGestureRecognizer.State.cancelled, or UIGestureRecognizer.State.ended state. In addition to calling the reset() method, UIKit automatically changes each gesture recognizer’s state property back to UIGestureRecognizer.State.possible so that it can respond to new event sequences.

## See Also

### Creating Custom Gesture Recognizers

Implementing a Discrete Gesture Recognizer

If your gesture involves a specific pattern of events, consider implementing a discrete gesture recognizer for it.

Implementing a Continuous Gesture Recognizer

For gestures that do not easily match a specific pattern, or when you want to use a gesture recognizer to gather touch input, create a continuous gesture recognizer.

