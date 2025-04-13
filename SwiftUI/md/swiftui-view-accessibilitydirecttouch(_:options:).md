

- SwiftUI
- View
-  accessibilityDirectTouch(\_:options:) 

Instance Method

# accessibilityDirectTouch(\_:options:)

Explicitly set whether this accessibility element is a direct touch area. Direct touch areas passthrough touch events to the app rather than being handled through an assistive technology, such as VoiceOver. The modifier accepts an optional `AccessibilityDirectTouchOptions` option set to customize the functionality of the direct touch area.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+tvOS 17.0+visionOS 1.0+watchOS 10.0+

``` source
nonisolated
func accessibilityDirectTouch(
    _ isDirectTouchArea: Bool = true,
    options: AccessibilityDirectTouchOptions = []
) -> ModifiedContent
```

## Discussion

For example, this is how a direct touch area would allow a VoiceOver user to interact with a view with a `rotationEffect` controlled by a `RotationGesture`. The direct touch area would require a user to activate the area before using the direct touch area.

```
var body: some View {
    Rectangle()
        .frame(width: 200, height: 200, alignment: .center)
        .rotationEffect(angle)
        .gesture(rotation)
        .accessibilityDirectTouch(options: .requiresActivation)
}
```

## See Also

### Making gestures accessible

func accessibilityActivationPoint(_:)

The activation point for an element is the location assistive technologies use to initiate gestures.

func accessibilityActivationPoint(_:isEnabled:)

The activation point for an element is the location assistive technologies use to initiate gestures.

func accessibilityDragPoint(_:description:)

The point an assistive technology should use to begin a drag interaction.

func accessibilityDragPoint(_:description:isEnabled:)

The point an assistive technology should use to begin a drag interaction.

func accessibilityDropPoint(_:description:)

The point an assistive technology should use to end a drag interaction.

func accessibilityDropPoint(_:description:isEnabled:)

The point an assistive technology should use to end a drag interaction.

func accessibilityZoomAction((AccessibilityZoomGestureAction) -> Void) -> ModifiedContent&lt;Self, AccessibilityAttachmentModifier>

Adds an accessibility zoom action to the view. Actions allow assistive technologies, such as VoiceOver, to interact with the view by invoking the action.

struct AccessibilityDirectTouchOptions

An option set that defines the functionality of a view’s direct touch area.

struct AccessibilityZoomGestureAction

Position and direction information of a zoom gesture that someone performs with an assistive technology like VoiceOver.

