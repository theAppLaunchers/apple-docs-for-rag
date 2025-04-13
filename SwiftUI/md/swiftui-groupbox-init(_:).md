

- SwiftUI
- GroupBox
-  init(\_:) 

Initializer

# init(\_:)

Creates a group box based on a style configuration.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+macOS 11.0+visionOS 1.0+

``` source
nonisolated
init(_ configuration: GroupBoxStyleConfiguration)
```

Available when `Label` is `GroupBoxStyleConfiguration.Label` and `Content` is `GroupBoxStyleConfiguration.Content`.

## Parameters 

`configuration`  

The properties of the group box instance being created.

## Discussion

Use this initializer within the makeBody(configuration:) method of a GroupBoxStyle instance to create a styled group box, with customizations, while preserving its existing style.

The following example adds a pink border around the group box, without overriding its current style:

```
struct PinkBorderGroupBoxStyle: GroupBoxStyle {
    func makeBody(configuration: Configuration) -> some View {
        GroupBox(configuration)
            .border(Color.pink)
    }
}
```

