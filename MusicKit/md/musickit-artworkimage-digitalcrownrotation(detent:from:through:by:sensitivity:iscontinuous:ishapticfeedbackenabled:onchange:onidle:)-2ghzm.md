

- MusicKit
- ArtworkImage
-  digitalCrownRotation(detent:from:through:by:sensitivity:isContinuous:isHapticFeedbackEnabled:onChange:onIdle:) 

Instance Method

# digitalCrownRotation(detent:from:through:by:sensitivity:isContinuous:isHapticFeedbackEnabled:onChange:onIdle:)

Tracks Digital Crown rotations by updating the specified binding.

MusicKitSwiftUIwatchOS 9.0+

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
) -> some View where V : BinaryInteger, V.Stride : BinaryInteger
```

## Parameters 

`binding`  

A binding to a value that updates when the user rotates the Digital Crown.

`minValue`  

Lower end of the range reported.

`maxValue`  

Upper end of the range reported.

`stride`  

The value settles on multiples of `stride`.

`sensitivity`  

How much the user needs to rotate the Digital Crown to move between two integer numbers.

`isContinuous`  

Controls if the value reported stops at `minValue` and `maxValue`, or if it should wrap around. Default is `false`.

`isHapticFeedbackEnabled`  

Controls the generation of haptic feedback when turning the Digital Crown. Default is `true`.

`onChange`  

A block that is called as the Digital Crown is rotated.

`onIdle`  

A block that is called when the Digital Crown has settled to an idle state.

## Discussion

Use this method to receive values on a binding you provides as the user turns the Digital Crown on Apple Watch. The example below receives changes to the binding value, starting at the `minValue` of `0` up to the `maxValue` of `100` in steps of `1` incrementing or decrementing depending on the direction that the user turns the Digital Crown, rolling over if the user exceeds the specified boundary values. The binding will always be updated to a value that is a multiple of the stride that is provided:

```
struct DigitalCrown: View {
    @State private var crownValue = 0.0
    @State private var selected = 0
    @State private var minValue = 0
    @State private var maxValue = 100
    @State private var stepAmount = 1
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

