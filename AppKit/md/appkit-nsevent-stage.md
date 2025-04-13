

- AppKit
- NSEvent
-  stage 

Instance Property

# stage

A value that indicates the stage of a pressure gesture event.

macOS 10.10.3+

``` source
var stage: Int { get }
```

## Discussion

Gesture events of type NSEvent.EventType.pressure can go through multiple stages. This property indicates the current stage of the event.

If this property has a value of `0`, there isn’t enough pressure to initiate or continue with the gesture. Effectively, this value will exist only when an event ends, as some level of pressure will be applied throughout the gesture.

A value of `1` indicates that the user applied enough pressure to represent a mouse-down event.

A value of `2` suggests that the user applied additional pressure beyond what the requirement for a typical mouse-down event. A stage value of `2` should generally be used to initiate a lookup or immediate action; for example, force clicking (pressing harder) on an element, such as a contact in an email message, to display a Quick Look window or to enter edit mode.

Typically, as a gesture event moves between stages, the user will receive light tactile feedback.

Stages do not always occur in sequence. For example, ending the gesture with a stage value of `2` may result in an immediate transition to a stage value of `0`. As such, the gesture event may skip over stage 1.

## See Also

### Related Documentation

enum EventType

Constants for the types of events that responder objects can handle.

case pressure

An event that reports a change in pressure on a pressure-sensitive device.

### Getting pressure information

var pressure: Float

A normalized value that indicates the degree of pressure applied to an appropriate input device.

var stageTransition: CGFloat

The transition value for the stage of a pressure gesture event.

var pressureBehavior: NSEvent.PressureBehavior

The behavior and progression for a pressure event.

enum PressureBehavior

These constants describe the behavior and progression of a pressure gesture.

