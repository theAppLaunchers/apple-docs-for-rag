

- AppKit
- NSButton
-  getPeriodicDelay(\_:interval:) 

Instance Method

# getPeriodicDelay(\_:interval:)

Returns by reference the delay and interval periods for a continuous button.

macOS

``` source
@MainActor
func getPeriodicDelay(
    _ delay: UnsafeMutablePointer,
    interval: UnsafeMutablePointer
)
```

## Parameters 

`delay`  

On return, the amount of time (in seconds) the button will pause before starting to periodically send action messages to the target object. The default delay is taken from a user’s default (60 seconds maximum). If the user hasn’t specified a default value, `delay` defaults to 0.4 seconds,

`interval`  

On return, the amount of time (in seconds) the button will pause between sending each action message. The default interval is taken from a user’s default (60 seconds maximum). If the user hasn’t specified a default value, `interval` defaults to 0.075 seconds.

## See Also

### Related Documentation

var isContinuous: Bool

A Boolean value indicating whether the receiver’s cell sends its action message continuously to its target during mouse tracking.

### Configuring Buttons

func setButtonType(NSButton.ButtonType)

Sets the button’s type, which affects its user interface and behavior when clicked.

func setPeriodicDelay(Float, interval: Float)

Sets the message delay and interval periods for a continuous button.

var contentTintColor: NSColor?

A tint color to use for the template image and text content.

var hasDestructiveAction: Bool

A Boolean value that defines whether a button’s action has a destructive effect.

var alternateTitle: String

The title that the button displays when the button is in an on state.

var attributedTitle: NSAttributedString

The title that the button displays in an off state, as an attributed string.

var attributedAlternateTitle: NSAttributedString

The title that the button displays as an attributed string when the button is in an on state.

var title: String

The title displayed on the button when it’s in an off state.

var symbolConfiguration: NSImage.SymbolConfiguration?

The combination of point size, weight, and scale to use when sizing and displaying symbol images.

var sound: NSSound?

The sound that plays when the user clicks the button.

var isSpringLoaded: Bool

A Boolean value that indicates whether spring loading is enabled for the button.

var maxAcceleratorLevel: Int

An integer value indicating the maximum pressure level for a button of type NSMultiLevelAcceleratorButton.

