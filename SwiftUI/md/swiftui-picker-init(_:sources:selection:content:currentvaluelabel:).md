

- SwiftUI
- Picker
-  init(\_:sources:selection:content:currentValueLabel:) 

Initializer

# init(\_:sources:selection:content:currentValueLabel:)

Creates a picker bound to a collection of bindings that generates its label from a string and accepts a custom current value label.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+tvOS 18.0+visionOS 2.0+watchOS 11.0+

``` source
nonisolated
init(
    _ title: S,
    sources: C,
    selection: KeyPath>,
    @ViewBuilder content: () -> Content,
    @ViewBuilder currentValueLabel: () -> some View
) where C : RandomAccessCollection, S : StringProtocol
```

Available when `Label` is `Text`, `SelectionValue` conforms to `Hashable`, and `Content` conforms to `View`.

Show all declarations

## Parameters 

`title`  

A string that describes the purpose of selecting an option.

`sources`  

A collection of values used as the source for displaying the Picker’s selection.

`selection`  

The key path of the values that determines the currently-selected options. When a user selects an option from the picker, the values at the key path of all items in the `sources` collection are updated with the selected option.

`content`  

A view that contains the set of options.

`currentValueLabel`  

A view that represents the current value of the picker.

## Discussion

If the wrapped values of the collection passed to `sources` are not all the same, some styles render the selection in a mixed state. The specific presentation depends on the style. For example, a Picker with a menu style uses dashes instead of checkmarks to indicate the selected values.

In the following example, a picker in a document inspector controls the thickness of borders for the currently-selected shapes, which can be of any number.

```
enum Thickness: String, CaseIterable, Identifiable {
    case thin
    case regular
    case thick

    var id: String { rawValue }
}

struct Border {
    var color: Color
    var thickness: Thickness
}

@State private var selectedObjectBorders = [
    Border(color: .black, thickness: .thin),
    Border(color: .red, thickness: .thick)
]

Picker(
    "Border Thickness",
    sources: $selectedObjectBorders,
    selection: \.thickness
) {
    ForEach(Thickness.allCases) { thickness in
        Text(thickness.rawValue)
    }
} currentValueLabel: {
     switch selectedObjectBorders.count {
        case 0: Text("None")
        case 1: Text(selectedObjectBorders[0].thickness.rawValue)
        default: Text("Multiple")
     }
}
```

This initializer creates a Text view on your behalf. See Text for more information about localizing strings.

