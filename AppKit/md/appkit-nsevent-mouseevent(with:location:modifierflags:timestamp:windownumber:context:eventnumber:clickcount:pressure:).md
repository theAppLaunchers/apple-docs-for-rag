

- AppKit
- NSEvent
-  mouseEvent(with:location:modifierFlags:timestamp:windowNumber:context:eventNumber:clickCount:pressure:) 

Type Method

# mouseEvent(with:location:modifierFlags:timestamp:windowNumber:context:eventNumber:clickCount:pressure:)

Creates and returns a new event object that describes a mouse-down, -up, -moved, or -dragged event.

macOS

``` source
class func mouseEvent(
    with type: NSEvent.EventType,
    location: NSPoint,
    modifierFlags flags: NSEvent.ModifierFlags,
    timestamp time: TimeInterval,
    windowNumber wNum: Int,
    context unusedPassNil: NSGraphicsContext?,
    eventNumber eNum: Int,
    clickCount cNum: Int,
    pressure: Float
) -> NSEvent?
```

## Parameters 

`type`  

One of the modifier key masks described in NSEvent.EventType, or an `NSInternalInconsistencyException` is raised.

`location`  

The cursor location in the base coordinate system of the window specified by `windowNum`.

`flags`  

An integer bit field containing any of the modifier key masks described in `Getting Unicode Values`, combined using the C bitwise OR operator.

`time`  

The time the event occurred in seconds since system startup.

`wNum`  

An integer that identifies the window device associated with the event, which is associated with the `NSWindow` that will receive the event.

`unusedPassNil`  

The display graphics context of the event. Pass `nil` for this parameter.

`eNum`  

An identifier for the new event. It’s normally taken from a counter for mouse events, which continually increases as the application runs.

`cNum`  

The number of mouse clicks associated with the mouse event.

`pressure`  

A value from `0.0` to `1.0` indicating the pressure applied to the input device on a mouse event, used for an appropriate device such as a graphics tablet. For devices that aren’t pressure-sensitive, the value should be either `0.0` or `1.0`.

## Return Value

The created `NSEvent` instance or `nil` if the instance could not be created.

## See Also

### Related Documentation

var clickCount: Int

The number of mouse clicks associated with a mouse-down or mouse-up event.

var eventNumber: Int

The counter value of the latest mouse or tracking-rectangle event object.

var systemUptime: TimeInterval

The amount of time the system has been awake since the last time it was restarted.

var pressure: Float

A normalized value that indicates the degree of pressure applied to an appropriate input device.

### Creating an event object

class func keyEvent(with: NSEvent.EventType, location: NSPoint, modifierFlags: NSEvent.ModifierFlags, timestamp: TimeInterval, windowNumber: Int, context: NSGraphicsContext?, characters: String, charactersIgnoringModifiers: String, isARepeat: Bool, keyCode: UInt16) -> NSEvent?

Creates and returns a new event object that describes a key event.

class func enterExitEvent(with: NSEvent.EventType, location: NSPoint, modifierFlags: NSEvent.ModifierFlags, timestamp: TimeInterval, windowNumber: Int, context: NSGraphicsContext?, eventNumber: Int, trackingNumber: Int, userData: UnsafeMutableRawPointer?) -> NSEvent?

Creates and returns a new event object that describes a tracking-rectangle or cursor-update event.

class func otherEvent(with: NSEvent.EventType, location: NSPoint, modifierFlags: NSEvent.ModifierFlags, timestamp: TimeInterval, windowNumber: Int, context: NSGraphicsContext?, subtype: Int16, data1: Int, data2: Int) -> NSEvent?

Creates and returns a new event object that describes a custom event.

init?(eventRef: UnsafeRawPointer)

Creates and returns a new event object for a Carbon event.

init?(cgEvent: CGEvent)

Creates and returns an event object for a Core Graphics event.

