

- MusicKit
- ArtworkImage
-  grayscale(\_:) 

Instance Method

# grayscale(\_:)

Adds a grayscale effect to this view.

MusicKitSwiftUIiOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
nonisolated
func grayscale(_ amount: Double) -> some View
```

## Parameters 

`amount`  

The intensity of grayscale to apply from 0.0 to less than 1.0. Values closer to 0.0 are more colorful, and values closer to 1.0 are less colorful.

## Return Value

A view that adds a grayscale effect to this view.

## Discussion

A grayscale effect reduces the intensity of colors in this view.

The example below shows a series of red squares with their grayscale effect increasing from 0 (reddest) to 99% (fully desaturated) in approximate 20% increments:

```
struct Saturation: View {
    var body: some View {
        HStack {
            ForEach(0..

