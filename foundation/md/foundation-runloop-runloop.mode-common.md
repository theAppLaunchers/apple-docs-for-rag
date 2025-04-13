

- Foundation
- RunLoop
- RunLoop.Mode
-  common 

Type Property

# common

A pseudo-mode that includes one or more other run loop modes.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.1+macOS 10.5+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
static let common: RunLoop.Mode
```

## Discussion

When you add an object to a run loop using this mode, the runloop monitors the object when running in any of the common modes. For details about adding a runloop mode to the set of common modes, see CFRunLoopAddCommonMode(_:_:).

## See Also

### System Run Loop Modes

static let `default`: RunLoop.Mode

The mode set to handle input sources other than connection objects.

static let eventTracking: RunLoop.Mode

The mode set when tracking events modally, such as a mouse-dragging loop.

static let modalPanel: RunLoop.Mode

The mode set when waiting for input from a modal panel, such as a save or open panel.

static let tracking: RunLoop.Mode

The mode set while tracking in controls takes place.

