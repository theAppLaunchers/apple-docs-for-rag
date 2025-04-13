

- HomeKit
-  HMCharacteristicTypeCurrentPosition 

Global Variable

# HMCharacteristicTypeCurrentPosition

The current position of a door, window, awning, or window covering.

iOS 9.0+iPadOS 9.0+Mac Catalyst 9.0+tvOS 10.0+visionOS 1.0+watchOS 2.0+

``` source
let HMCharacteristicTypeCurrentPosition: String
```

## Discussion

The corresponding value is an integer percentage. A value of `0` indicates a door or window is fully closed, or that awnings or shades permit the least possible light. A value of `100` indicates the opposite.

## See Also

### Doors and windows

let HMCharacteristicTypeCurrentDoorState: String

The current door state.

let HMCharacteristicTypeTargetDoorState: String

The target door state.

let HMCharacteristicTypeTargetPosition: String

The target position of a door, window, awning, or window covering.

let HMCharacteristicTypePositionState: String

The position of an accessory like a door, window, awning, or window covering.

let HMCharacteristicTypeStatusJammed: String

An indicator of whether an accessory is jammed.

let HMCharacteristicTypeHoldPosition: String

A control for holding the position of an accessory like a door or window.

let HMCharacteristicTypeSlatType: String

The type of slat on an accessory like a window or a fan.

let HMCharacteristicTypeCurrentSlatState: String

The current state of slats on an accessory like a window or a fan.

