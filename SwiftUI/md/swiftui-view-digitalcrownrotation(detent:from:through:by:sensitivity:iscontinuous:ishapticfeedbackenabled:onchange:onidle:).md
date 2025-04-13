

- SwiftUI
- View
-  digitalCrownRotation(detent:from:through:by:sensitivity:isContinuous:isHapticFeedbackEnabled:onChange:onIdle:) 

Instance Method

# digitalCrownRotation(detent:from:through:by:sensitivity:isContinuous:isHapticFeedbackEnabled:onChange:onIdle:)

Tracks Digital Crown rotations by updating the specified binding.

watchOS 9.0+

``` source
nonisolated
func digitalCrownRotation(
    detent: Binding,
    from minValue: V,
    through maxValue: V,
    by stride: V.Stride,
    sensitivity: DigitalCrownRotationalSensitivity = .high,
    isContinuous: Bool = false,
    isHapticFeedbackEnabled: Bool = true,
    onChange: @escaping (DigitalCrownEvent) -> Void = { _ in },
    onIdle: @escaping () -> Void = { }
) -> some View where V : BinaryFloatingPoint, V.Stride : BinaryFloatingPoint
```

Show all declarations

## Parameters 

`detent`  

A binding to a value that updates when the user rotates the Digital Crown.

`minValue`  

Lower end of the range reported.

`maxValue`  

Upper end of the range reported.

`stride`  

The value settles on multiples of `stride`.

`sensitivity`  

How much the user needs to rotate the Digital Crown to move between two detents.

`isContinuous`  

Controls if the value reported stops at `minValue` and `maxValue`, or if it should wrap around. Default is `false`.

`isHapticFeedbackEnabled`  

Controls the generation of haptic feedback when turning the Digital Crown. Default is `true`.

`onChange`  

A block that is called as the Digital Crown is rotated.

`onIdle`  

A block that is called when the Digital Crown has settled to an idle state.

## Discussion

Use this method to receive values on a binding you provide as the user turns the Digital Crown on Apple Watch. The example below receives changes to the binding value, starting at the `minValue` of `0.0` up to the `maxValue` of `10.0` in steps of `0.1` incrementing or decrementing depending on the direction that the user turns the Digital Crown, rolling over if the user exceeds the specified boundary values. The binding will always be updated to a value that is a multiple of the stride that is provided:

```
struct DigitalCrown: View {
    @State private var crownValue = 0.0
    @State private var selected = 0.0
    @State private var minValue = 0.0
    @State private var maxValue = 10.0
    @State private var stepAmount = 0.1
    @State private var velocity = 0.0
    @State private var isIdle = true

    var body: some View {
        Text("Received Value:\(crownValue, specifier: "%.2f")")
            .focusable()
            .digitalCrownRotation(detent: $selected,
                                  from: minValue,
                                  through: maxValue,
                                  by: stepAmount,
                                  sensitivity: .low,
                                  isContinuous: true
            ) { crownEvent in
                isIdle = false
                crownValue = crownEvent.offset
                velocity = crownEvent.velocity
            } onIdle: {
                isIdle = true
            }
    }
}
```

## See Also

### Interacting with the Digital Crown

func digitalCrownAccessory(Visibility) -> some View

Specifies the visibility of Digital Crown accessory Views on Apple Watch.

func digitalCrownAccessory&lt;Content>(content: () -> Content) -> some View

Places an accessory View next to the Digital Crown on Apple Watch.

func digitalCrownRotation&lt;V>(Binding&lt;V>, from: V, through: V, sensitivity: DigitalCrownRotationalSensitivity, isContinuous: Bool, isHapticFeedbackEnabled: Bool, onChange: (DigitalCrownEvent) -> Void, onIdle: () -> Void) -> some View

Tracks Digital Crown rotations by updating the specified binding.

func digitalCrownRotation&lt;V>(Binding&lt;V>, onChange: (DigitalCrownEvent) -> Void, onIdle: () -> Void) -> some View

Tracks Digital Crown rotations by updating the specified binding.

func digitalCrownRotation&lt;V>(Binding&lt;V>) -> some View

Tracks Digital Crown rotations by updating the specified binding.

func digitalCrownRotation&lt;V>(Binding&lt;V>, from: V, through: V, by: V.Stride?, sensitivity: DigitalCrownRotationalSensitivity, isContinuous: Bool, isHapticFeedbackEnabled: Bool) -> some View

Tracks Digital Crown rotations by updating the specified binding.

struct DigitalCrownEvent

An event emitted when the user rotates the Digital Crown.

enum DigitalCrownRotationalSensitivity

The amount of Digital Crown rotation needed to move between two integer numbers.

