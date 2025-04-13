

- SwiftUI
- Animation
-  delay(\_:) 

Instance Method

# delay(\_:)

Delays the start of the animation by the specified number of seconds.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
func delay(_ delay: TimeInterval) -> Animation
```

## Parameters 

`delay`  

The number of seconds to delay the start of the animation.

## Return Value

An animation with a delayed start.

## Discussion

Use this method to delay the start of an animation. For example, the following code animates the height change of two capsules. Animation of the first Capsule begins immediately. However, animation of the second one doesn’t begin until a half second later.

```
struct ContentView: View {
    @State private var adjustBy = 100.0

    var body: some View {
        VStack(spacing: 40) {
            HStack(alignment: .bottom) {
                Capsule()
                    .frame(width: 50, height: 175 - adjustBy)
                    .animation(.easeInOut, value: adjustBy)
                Capsule()
                    .frame(width: 50, height: 175 + adjustBy)
                    .animation(.easeInOut.delay(0.5), value: adjustBy)
            }

            Button("Animate") {
                adjustBy *= -1
            }
        }
    }
}
```

 Video with custom controls. 

 Content description: A video that shows two capsules side by side that animate using the ease-in ease-out animation. The capsule on the left is short, while the capsule on the right is tall. As they animate, the short capsule grows upwards to match the height of the tall capsule. Then the tall capsule shrinks to match the original height of the short capsule. Then the capsule on the left shrinks to its original height, followed by the capsule on the right growing to its original height. 

Play 

## See Also

### Configuring an animation

func repeatCount(Int, autoreverses: Bool) -> Animation

Repeats the animation for a specific number of times.

func repeatForever(autoreverses: Bool) -> Animation

Repeats the animation for the lifespan of the view containing the animation.

func speed(Double) -> Animation

Changes the duration of an animation by adjusting its speed.

