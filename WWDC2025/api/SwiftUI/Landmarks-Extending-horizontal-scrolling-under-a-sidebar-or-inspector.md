*   [SwiftUI](/documentation/swiftui)
*   [Landmarks: Building an app with Liquid Glass](/documentation/swiftui/landmarks-building-an-app-with-liquid-glass)
*   Landmarks: Extending horizontal scrolling under a sidebar or inspector Beta

Sample Code

# Landmarks: Extending horizontal scrolling under a sidebar or inspector

Improve your horizontal scrollbar’s appearance by extending it under a sidebar or inspector.

[Download](https://docs-assets.developer.apple.com/published/10d19597bd72/LandmarksBuildingAnAppWithLiquidGlass.zip)

iOS 26.0+BetaiPadOS 26.0+BetamacOS 26.0+BetaXcode 26.0+Beta

## [Overview](/documentation/SwiftUI/Landmarks-Extending-horizontal-scrolling-under-a-sidebar-or-inspector#Overview)

The Landmarks app lets people explore interesting sites around the world. Whether it’s a national park near their home or a far-flung location on a different continent, the app provides a way for people to organize and mark their adventures and receive custom activity badges along the way.

This sample demonstrates how to extend horizontal scrolling under a sidebar or inspector. Within each continent section in `LandmarksView`, an instance of `LandmarkHorizontalListView` shows a horizontally scrolling list of landmark views. When open, the landmark views can scroll underneath the sidebar or inspector.

![An image of the landmarks view on an iPad, with the sidebar visible and some landmarks visible under the sidebar.](https://docs-assets.developer.apple.com/published/a4b11a4a06f283b210c25071788c472e/Landmarks-Building-an-app-with-Liquid-Glass-3%402x.png)

## [Configure the scroll view](/documentation/SwiftUI/Landmarks-Extending-horizontal-scrolling-under-a-sidebar-or-inspector#Configure-the-scroll-view)

To achieve this effect, the sample configures the `LandmarkHorizontalListView` so it touches the leading and trailing edges. When a scroll view touches the sidebar or inspector, the system automatically adjusts it to scroll under the sidebar or inspector and then off the edge of the screen.

The sample adds a [`Spacer`](/documentation/swiftui/spacer) at the beginning of the [`ScrollView`](/documentation/swiftui/scrollview) to inset the content so it aligns with the title padding:

```

```
ScrollView(.horizontal, showsIndicators: false) {
    LazyHStack(spacing: Constants.standardPadding) {
        Spacer()
            .frame(width: Constants.standardPadding)
        ForEach(landmarkList) { landmark in
            //...
        }
    }
}
```

```

## [See Also](/documentation/SwiftUI/Landmarks-Extending-horizontal-scrolling-under-a-sidebar-or-inspector#see-also)

### [App features](/documentation/SwiftUI/Landmarks-Extending-horizontal-scrolling-under-a-sidebar-or-inspector#App-features)

[

Landmarks: Applying a background extension effect](/documentation/swiftui/landmarks-applying-a-background-extension-effect)

Configure an image to blur and extend under a sidebar or inspector panel.

[

Landmarks: Refining the system provided Liquid Glass effect in toolbars](/documentation/swiftui/landmarks-refining-the-system-provided-glass-effect-in-toolbars)

Organize toolbars into related groupings to improve their appearance and utility.

[

Landmarks: Displaying custom activity badges](/documentation/swiftui/landmarks-displaying-custom-activity-badges)

Provide people with a way to mark their adventures by displaying animated custom activity badges.

Beta Software

This documentation contains preliminary information about an API or technology in development. This information is subject to change, and software implemented according to this documentation should be tested with final operating system software.

[Learn more about using Apple's beta software](https://developer.apple.com/support/beta-software/)