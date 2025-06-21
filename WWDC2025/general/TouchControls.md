Framework

# Touch Controls

Integrate on-screen touch controls into your Metal-based games.

iOS 26.0+BetaiPadOS 26.0+BetaMac Catalyst 26.0+Beta

## [Overview](/documentation/TouchControls#overview)

Use Touch Controls to add custom and interactive touch controls for your games. The framework offers a suite of controls that enable support for a variety of control schemes, for example, buttons, direction pads, thumbsticks, throttles, and touchpads. The Game Controller framework supports each control and surfaces them through a [`GCController`](/documentation/GameController/GCController) instance.

Use the [`TCTouchController`](/documentation/touchcontrols/tctouchcontroller) class as the central point to manage and render your touch controls. To configure the appearance of your controls, use [`TCControlVisuals`](/documentation/touchcontrols/tccontrolvisuals) and [`TCSpriteRenderer`](/documentation/touchcontrols/tcspriterenderer). Use [`TCControlSystemVisualsProvider`](/documentation/touchcontrols/tccontrolsystemvisualsprovider) to create a consistent look and feel with system-provided assets.

## [Topics](/documentation/TouchControls#topics)

### [Essentials](/documentation/TouchControls#Essentials)

```swift
```swift
```swift
```swift
class TCTouchController
```
```

An object that allows you to create and customize on-screen touch controls for a game that uses Metal.
```
```

### [Controls](/documentation/TouchControls#Controls)

```swift
```swift
```swift
```swift
protocol TCControl
```
```

A protocol that defines the base properties and methods for all touch controls.
```
```swift
```swift
```swift
class TCButton
```
```

A control that represents a single on-screen button.
```
```swift
```swift
```swift
class TCDirectionPad
```
```

An object that represents a direction pad.
```
```swift
```swift
```swift
class TCThumbstick
```
```

Represents a single on-screen thumbstick.
```
```swift
```swift
```swift
class TCThrottle
```
```

Represents a single on-screen throttle - a one axis input.
```
```swift
```swift
```swift
class TCTouchpad
```
```

Represents a single on-screen touchpad that reports absolute coordinates or delta movements.
```
```

### [Visuals](/documentation/TouchControls#Visuals)

```swift
```swift
```swift
```swift
class TCControlVisuals
```
```

Represents the visual elements of a touch control.
```
```swift
```swift
```swift
class TCSpriteRenderer
```
```

A renderer for drawing sprites using Metal.
```
```

### [System visuals](/documentation/TouchControls#System-visuals)

```swift
```swift
```swift
```swift
class TCControlSystemVisualsProvider
```
```

Provides system-defined visuals for touch controls.
```
```swift
```swift
```swift
enum TCButtonVisualShape
```
```

Defines the visual shape of a button.
```
```swift
```swift
```swift
enum TCDirectionPadVisualStyle
```
```

Defines the visual style of a direction pad.
```
```swift
```swift
```swift
enum TCDirectionPadVisualDirection
```
```

Defines the direction of a direction pad visual.
```
```

### [Collision](/documentation/TouchControls#Collision)

```swift
```swift
```swift
```swift
protocol TCCollider
```
```

A protocol defining the collider properties for a control.
```
```swift
```swift
```swift
enum TCColliderType
```
```

Defines the type of collider.
```
```swift
```swift
```swift
class TCRectCollider
```
```

A rectangular collider.
```
```swift
```swift
```swift
class TCCircleCollider
```
```

A circular collider.
```
```swift
```swift
```swift
class TCRegionCollider
```
```

A collider that covers a specific region of the touch controller.
```
```swift
```swift
```swift
enum TCRegionColliderRegion
```
```

Defines the region of the touch controller that the `TCRegionCollider` represents.
```
```

### [Classes](/documentation/TouchControls#Classes)

```swift
```swift
```swift
```swift
class TCButtonDescriptor
```
```

A descriptor for configuring a button.
```
```swift
```swift
```swift
class TCControlLabel
```
```

A label you associate with a touch control and provides a semantic description.
```
```swift
```swift
```swift
class TCDirectionPadDescriptor
```
```

A descriptor for configuring a directional pad.
```
```swift
```swift
```swift
class TCThrottleDescriptor
```
```

A descriptor for configuring a throttle.
```
```swift
```swift
```swift
class TCThumbstickDescriptor
```
```

A descriptor for configuring a thumbstick.
```
```swift
```swift
```swift
class TCTouchControllerDescriptor
```
```

A descriptor for configuring a touch controller.
```
```swift
```swift
```swift
class TCTouchpadDescriptor
```
```

A descriptor for configuring a touchpad.
```
```

### [Protocols](/documentation/TouchControls#Protocols)

```swift
```swift
```swift
```swift
protocol TCTransform
```
```

A protocol defining the transform properties for a control.
```
```

### [Enumerations](/documentation/TouchControls#Enumerations)

```swift
```swift
```swift
```swift
enum TCControlLabelType
```
```

Defines the type of control label.
```
```swift
```swift
```swift
enum TCThrottleOrientation
```
```

Defines the orientation of the throttle.
```
```swift
```swift
```swift
enum TCTransformAnchor
```
```

Defines the anchor point for a transform.
```
```

Beta Software

This documentation contains preliminary information about an API or technology in development. This information is subject to change, and software implemented according to this documentation should be tested with final operating system software.

[Learn more about using Apple's beta software](https://developer.apple.com/support/beta-software/)