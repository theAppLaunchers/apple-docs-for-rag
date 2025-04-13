

- SwiftUI
-  DisclosureGroup 

Structure

# DisclosureGroup

A view that shows or hides another content view, based on the state of a disclosure control.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+macOS 11.0+visionOS 1.0+

``` source
struct DisclosureGroup where Label : View, Content : View
```

## Mentioned in 

Displaying data in lists

## Overview

A disclosure group view consists of a label to identify the contents, and a control to show and hide the contents. Showing the contents puts the disclosure group into the “expanded” state, and hiding them makes the disclosure group “collapsed”.

In the following example, a disclosure group contains two toggles and an embedded disclosure group. The top level disclosure group exposes its expanded state with the bound property, `topLevelExpanded`. By expanding the disclosure group, the user can use the toggles to update the state of the `toggleStates` structure.

```
struct ToggleStates {
    var oneIsOn: Bool = false
    var twoIsOn: Bool = true
}
@State private var toggleStates = ToggleStates()
@State private var topExpanded: Bool = true

var body: some View {
    DisclosureGroup("Items", isExpanded: $topExpanded) {
        Toggle("Toggle 1", isOn: $toggleStates.oneIsOn)
        Toggle("Toggle 2", isOn: $toggleStates.twoIsOn)
        DisclosureGroup("Sub-items") {
            Text("Sub-item 1")
        }
    }
}
```

## Topics

### Creating a disclosure group

init(_:content:)

Creates a disclosure group, using a provided localized string key to create a text view for the label.

init(content: () -> Content, label: () -> Label)

Creates a disclosure group with the given label and content views.

init(_:isExpanded:content:)

Creates a disclosure group, using a provided localized string key to create a text view for the label, and a binding to the expansion state (expanded or collapsed).

init(isExpanded: Binding&lt;Bool>, content: () -> Content, label: () -> Label)

Creates a disclosure group with the given label and content views, and a binding to the expansion state (expanded or collapsed).

## Relationships

### Conforms To

- View

## See Also

### Disclosing information progressively

struct OutlineGroup

A structure that computes views and disclosure groups on demand from an underlying collection of tree-structured, identified data.

func disclosureGroupStyle&lt;S>(S) -> some View

Sets the style for disclosure groups within this view.

