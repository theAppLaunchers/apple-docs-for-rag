

- SwiftUI
- View
-  toolbarForegroundStyle(\_:for:) 

Instance Method

# toolbarForegroundStyle(\_:for:)

Specifies the preferred foreground style of bars managed by SwiftUI.

watchOS 9.0+

``` source
nonisolated
func toolbarForegroundStyle(
    _ style: S,
    for bars: ToolbarPlacement...
) -> some View where S : ShapeStyle
```

## Discussion

This examples shows a view that renders the navigation bar with a blue foreground color.

```
NavigationStack {
    ContentView()
        .navigationTitle("Blue")
        .toolbarForegroundStyle(
            .blue, for: .navigationBar)
}
```

## See Also

### Styling a toolbar

func toolbarBackground(_:for:)

Specifies the preferred shape style of the background of a bar managed by SwiftUI.

func toolbarColorScheme(ColorScheme?, for: ToolbarPlacement...) -> some View

Specifies the preferred color scheme of a bar managed by SwiftUI.

func windowToolbarStyle&lt;S>(S) -> some Scene

Sets the style for the toolbar defined within this scene.

protocol WindowToolbarStyle

A specification for the appearance and behavior of a window’s toolbar.

var toolbarLabelStyle: ToolbarLabelStyle?

The label style to apply to controls within a toolbar.

struct ToolbarLabelStyle

The label style of a toolbar.

