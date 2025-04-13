

- FinanceKitUI
- AddOrderToWalletButton
-  toolbarColorScheme(\_:for:) 

Instance Method

# toolbarColorScheme(\_:for:)

Specifies the preferred color scheme of a bar managed by SwiftUI.

FinanceKitUISwiftUIiOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+watchOS 9.0+

``` source
nonisolated
func toolbarColorScheme(
    _ colorScheme: ColorScheme?,
    for bars: ToolbarPlacement...
) -> some View
```

## Parameters 

`colorScheme`  

The preferred color scheme of the background of the bar.

`bars`  

The bars to update the color scheme of or `ToolbarPlacement/automatic` if empty.

## Discussion

The preferred color scheme flows up to the nearest container that renders a bar. This could be a `NavigationView` or `TabView` in iOS, or the root view of a `WindowGroup` in macOS. Pass in a value of nil to match the current system’s color scheme.

This examples shows a view that renders the navigation bar with a blue background and dark color scheme:

```
TabView {
    NavigationView {
        ContentView()
            .toolbarBackground(.blue)
            .toolbarColorScheme(.dark)
    }
    // other tabs...
}
```

You can provide multiple `ToolbarPlacement` instances to customize multiple bars at once.

```
TabView {
    NavigationView {
        ContentView()
            .toolbarBackground(
                .blue, for: .navigationBar, .tabBar)
            .toolbarColorScheme(
                .dark, for: .navigationBar, .tabBar)
    }
}
```

Note that the provided color scheme is only respected while a background is visible in the requested bar. As the background becomes visible, the bar transitions from the color scheme of the app to the requested color scheme. You can ensure that the color scheme is always respected by specifying that the background of the bar always be visible.

```
NavigationView {
    ContentView()
        .toolbarBackground(.visible)
        .toolbarColorScheme(.dark)
}
```

Depending on the specified bars, the requested color scheme may not be able to be fullfilled.

