

- SwiftUI
- PickerStyle
-  palette 

Type Property

# palette

A picker style that presents the options as a row of compact elements.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+visionOS 1.0+

``` source
static var palette: PalettePickerStyle { get }
```

Available when `Self` is `PalettePickerStyle`.

## Discussion

Note

When used outside of menus, this style is rendered as a segmented picker. If that is the intended usage, consider segmented instead.

For each option’s label, use one symbol per item, if you add more than 6 options, the picker scrolls horizontally on iOS.

The following example creates a palette picker:

```
enum Reaction: Identifiable, CaseIterable {
    case thumbsup, thumbsdown, heart, questionMark
    var id: Self { self }
}

@State private var selection: Reaction? = .none

var body: some View {
    Menu("Reactions") {
        Picker("Palette", selection: $selection) {
            Label("Thumbs up", systemImage: "hand.thumbsup")
                .tag(Reaction.thumbsup)
            Label("Thumbs down", systemImage: "hand.thumbsdown")
                .tag(Reaction.thumbsdown)
            Label("Like", systemImage: "heart")
                .tag(Reaction.heart)
            Label("Question mark", systemImage: "questionmark")
                .tag(Reaction.questionMark)
        }
        .pickerStyle(.palette)
        Button("Reply...") { ... }
    }
}
```

Palette pickers will display the selection of untinted SF Symbols or template images by applying the system tint. For tinted SF Symbols, a stroke is outlined around the symbol upon selection. If you would like to supply a particular image (or SF Symbol) to signify selection, we suggest using custom. This deactivates any system selection behavior, allowing the provided image to solely indicate selection instead.

The following example creates a palette picker that disables the system selection behaviour:

```
Menu {
    Picker("Palettes", selection: $selection) {
        ForEach(palettes) { palette in
            Label(palette.title, systemImage: selection == palette ?
                  "circle.dashed.inset.filled" : "circle.fill")
            .tint(palette.tint)
            .tag(palette)
        }
    }
    .pickerStyle(.palette)
    .paletteSelectionEffect(.custom)
} label: {
    ...
}
```

If a specific SF Symbol variant is preferable instead, use symbolVariant(_:):

```
Menu {
    Picker("Flags", selection: $selectedFlag) {
        ForEach(flags) { flag in
            Label(flag.title, systemImage: "flag")
                .tint(flag.color)
                .tag(flag)
        }
    }
    .pickerStyle(.palette)
    .paletteSelectionEffect(.symbolVariant(.slash))
} label: {
    ...
}
```

To apply this style to a picker, or to a view that contains pickers, use the pickerStyle(_:) modifier.

## See Also

### Getting built-in picker styles

static var automatic: DefaultPickerStyle

The default picker style, based on the picker’s context.

static var inline: InlinePickerStyle

A `PickerStyle` where each option is displayed inline with other views in the current container.

static var menu: MenuPickerStyle

A picker style that presents the options as a menu when the user presses a button, or as a submenu when nested within a larger menu.

static var navigationLink: NavigationLinkPickerStyle

A picker style represented by a navigation link that presents the options by pushing a List-style picker view.

static var radioGroup: RadioGroupPickerStyle

A picker style that presents the options as a group of radio buttons.

static var segmented: SegmentedPickerStyle

A picker style that presents the options in a segmented control.

static var wheel: WheelPickerStyle

A picker style that presents the options in a scrollable wheel that shows the selected option and a few neighboring options.

