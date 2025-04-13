

- ManagedAppDistribution
- ManagedAppView
-  onTapGesture(count:perform:) 

Instance Method

# onTapGesture(count:perform:)

Adds an action to perform when this view recognizes a tap gesture.

ManagedAppDistributionSwiftUIiOS 13.0+iPadOS 13.0+macOS 10.15+tvOS 16.0+watchOS 6.0+

``` source
nonisolated
func onTapGesture(
    count: Int = 1,
    perform action: @escaping () -> Void
) -> some View
```

## Parameters 

`count`  

The number of taps or clicks required to trigger the action closure provided in `action`. Defaults to `1`.

`action`  

The action to perform.

## Discussion

Use this method to perform the specified `action` when the user clicks or taps on the view or container `count` times.

Note

If you create a control that’s functionally equivalent to a `Button`, use `ButtonStyle` to create a customized button instead.

In the example below, the color of the heart images changes to a random color from the `colors` array whenever the user clicks or taps on the view twice:

```
struct TapGestureExample: View {
    let colors: [Color] = [.gray, .red, .orange, .yellow,
                           .green, .blue, .purple, .pink]
    @State private var fgColor: Color = .gray

    var body: some View {
        Image(systemName: "heart.fill")
            .resizable()
            .frame(width: 200, height: 200)
            .foregroundColor(fgColor)
            .onTapGesture(count: 2) {
                fgColor = colors.randomElement()!
            }
    }
}
```

