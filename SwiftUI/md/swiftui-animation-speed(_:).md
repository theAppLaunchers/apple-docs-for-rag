

- SwiftUI
- Animation
-  speed(\_:) 

Instance Method

# speed(\_:)

Changes the duration of an animation by adjusting its speed.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
func speed(_ speed: Double) -> Animation
```

## Parameters 

`speed`  

The speed at which SwiftUI performs the animation.

## Return Value

An animation with the adjusted speed.

## Discussion

Setting the speed of an animation changes the duration of the animation by a factor of `speed`. A higher speed value causes a faster animation sequence due to a shorter duration. For example, a one-second animation with a speed of `2.0` completes in half the time (half a second).

```
struct ContentView: View {
    @State private var adjustBy = 100.0

    private var oneSecondAnimation: Animation {
       .easeInOut(duration: 1.0)
    }

    var body: some View {
        VStack(spacing: 40) {
            HStack(alignment: .bottom) {
                Capsule()
                    .frame(width: 50, height: 175 - adjustBy)
                Capsule()
                    .frame(width: 50, height: 175 + adjustBy)
            }
            .animation(oneSecondAnimation.speed(2.0), value: adjustBy)

            Button("Animate") {
                adjustBy *= -1
            }
        }
    }
}
```

 Video with custom controls. 

 Content description: A video that shows two capsules side by side that animate using the ease-in ease-out animation. The capsule on the left is short, while the capsule on the right is tall. They animate for half a second with the short capsule growing upwards to match the height of the tall capsule. Then the tall capsule shrinks to match the original height of the short capsule. For another half second, the capsule on the left shrinks to its original height, followed by the capsule on the right growing to its original height. 

Play 

Setting `speed` to a lower number slows the animation, extending its duration. For example, a one-second animation with a speed of `0.25` takes four seconds to complete.

```
struct ContentView: View {
    @State private var adjustBy = 100.0

    private var oneSecondAnimation: Animation {
       .easeInOut(duration: 1.0)
    }

    var body: some View {
        VStack(spacing: 40) {
            HStack(alignment: .bottom) {
                Capsule()
                    .frame(width: 50, height: 175 - adjustBy)
                Capsule()
                    .frame(width: 50, height: 175 + adjustBy)
            }
            .animation(oneSecondAnimation.speed(0.25), value: adjustBy)

            Button("Animate") {
                adjustBy *= -1
            }
        }
    }
}
```

 Video with custom controls. 

 Content description: A video that shows two capsules side by side that animate using the ease-in ease-out animation. The capsule on the left is short, while the right-side capsule is tall. They animate for four seconds with the short capsule growing upwards to match the height of the tall capsule. Then the tall capsule shrinks to match the original height of the short capsule. For another four seconds, the capsule on the left shrinks to its original height, followed by the capsule on the right growing to its original height. 

Play 

## See Also

### Configuring an animation

func delay(TimeInterval) -> Animation

Delays the start of the animation by the specified number of seconds.

func repeatCount(Int, autoreverses: Bool) -> Animation

Repeats the animation for a specific number of times.

func repeatForever(autoreverses: Bool) -> Animation

Repeats the animation for the lifespan of the view containing the animation.

