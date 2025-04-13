

- SwiftUI
-  ColorPicker 

Structure

# ColorPicker

A control used to select a color from the system color picker UI.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+macOS 11.0+visionOS 1.0+

``` source
struct ColorPicker where Label : View
```

## Overview

The color picker provides a color well that shows the currently selected color, and displays the larger system color picker that allows users to select a new color.

By default color picker supports colors with opacity; to disable opacity support, set the `supportsOpacity` parameter to `false`. In this mode the color picker won’t show controls for adjusting the opacity of the selected color, and strips out opacity from any color set programmatically or selected from the user’s system favorites.

You use `ColorPicker` by embedding it inside a view hierarchy and initializing it with a title string and a Binding to a Color:

```
struct FormattingControls: View {
    @State private var bgColor =
        Color(.sRGB, red: 0.98, green: 0.9, blue: 0.2)

    var body: some View {
        VStack {
            ColorPicker("Alignment Guides", selection: $bgColor)
        }
    }
}
```

## Topics

### Creating a color picker

init(_:selection:supportsOpacity:)

Creates a color picker with a text label generated from a title string key.

init(selection:supportsOpacity:label:)

Creates an instance that selects a color.

## Relationships

### Conforms To

- View

