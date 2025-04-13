

- AppKit
- NSEvent
-  pressure 

Instance Property

# pressure

A normalized value that indicates the degree of pressure applied to an appropriate input device.

macOS

``` source
var pressure: Float { get }
```

## Discussion

For input devices that are pressure-sensitive, the value is increased as pressure is applied to the device.

For NSEvent.EventType.pressure events, pressure value relates to the current stage of the gesture event. Each stage has its own pressure curve. For example, pressure ranges from `0.0` through `1.0` for a stage 1 event, and `0.0` through `1.0` for a stage 2 event. Pressure readings should be retrieved for a single stage of a gesture only, and should not be combined to achieve a wider range of pressure levels. In most cases, retrieving pressure during stage 1 is sufficient and appropriate for supporting variable input. Stage 1 pressure is the most physically comfortable for the user. Stage 2 pressure should only be used in rare circumstances where additional tactile feedback is necessary prior to retrieving pressure level.

For input devices that aren’t pressure-sensitive, the value is either `0.0` or `1.0`. An internalInconsistencyException exception is raised if this property is accessed on an event other than a mouse-up, mouse-down, mouse-drag, NSTabletPoint, or NSEvent.EventType.pressure event.

For tablet pointing devices that are in proximity, the pressure value is `0.0` if the user is not actually touching the tablet.

Pressure is not intended to measure weight.

## See Also

### Related Documentation

class func mouseEvent(with: NSEvent.EventType, location: NSPoint, modifierFlags: NSEvent.ModifierFlags, timestamp: TimeInterval, windowNumber: Int, context: NSGraphicsContext?, eventNumber: Int, clickCount: Int, pressure: Float) -> NSEvent?

Creates and returns a new event object that describes a mouse-down, -up, -moved, or -dragged event.

enum EventType

Constants for the types of events that responder objects can handle.

var rotation: Float

The rotation in degrees of the tablet pointing device associated with this event.

case pressure

An event that reports a change in pressure on a pressure-sensitive device.

### Getting pressure information

var stage: Int

A value that indicates the stage of a pressure gesture event.

var stageTransition: CGFloat

The transition value for the stage of a pressure gesture event.

var pressureBehavior: NSEvent.PressureBehavior

The behavior and progression for a pressure event.

enum PressureBehavior

These constants describe the behavior and progression of a pressure gesture.

