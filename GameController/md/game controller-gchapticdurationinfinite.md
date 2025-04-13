

- Game Controller
-  GCHapticDurationInfinite 

Global Variable

# GCHapticDurationInfinite

An infinite duration for a haptics event.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+macOS 11.0+tvOS 14.0+visionOS 1.0+

``` source
let GCHapticDurationInfinite: Float
```

## Discussion

Use this constant to create a CHHapticEvent object with an infinite duration. For example, create an infinite haptic event that you update in a loop to adjust a controller’s motor intensity.

## See Also

### Creating a haptics engine

func createEngine(withLocality: GCHapticsLocality) -> CHHapticEngine?

Creates a haptics engine with the specified locality.

