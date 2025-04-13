

- MusicKit
- ArtworkImage
-  contrast(\_:) 

Instance Method

# contrast(\_:)

Sets the contrast and separation between similar colors in this view.

MusicKitSwiftUIiOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
nonisolated
func contrast(_ amount: Double) -> some View
```

## Parameters 

`amount`  

The intensity of color contrast to apply. negative values invert colors in addition to applying contrast.

## Return Value

A view that applies color contrast to this view.

## Discussion

Apply contrast to a view to increase or decrease the separation between similar colors in the view.

In the example below, the `contrast(_:)` modifier is applied to a set of red squares each containing a contrasting green inner circle. At each step in the loop, the `contrast(_:)` modifier changes the contrast of the circle/square view in 20% increments. This ranges from -20% contrast (yielding inverted colors — turning the red square to pale-green and the green circle to mauve), to neutral-gray at 0%, to 100% contrast (bright-red square / bright-green circle). Applying negative contrast values, as shown in the -20% square, will apply contrast in addition to inverting colors.

```
struct CircleView: View {
    var body: some View {
        Circle()
            .fill(Color.green)
            .frame(width: 25, height: 25, alignment: .center)
    }
}

struct Contrast: View {
    var body: some View {
        HStack {
            ForEach(-1..

