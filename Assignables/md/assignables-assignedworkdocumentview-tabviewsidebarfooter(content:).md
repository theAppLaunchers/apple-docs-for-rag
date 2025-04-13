

- Assignables
- AssignedWorkDocumentView
-  tabViewSidebarFooter(content:) 

Instance Method

# tabViewSidebarFooter(content:)

Adds a custom footer to the sidebar of a tab view.

AssignablesSwiftUIiOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+visionOS 2.0+

``` source
nonisolated
func tabViewSidebarFooter(@ViewBuilder content: () -> Content) -> some View where Content : View
```

## Discussion

The footer appears at the bottom of the sidebar after any tab labels and can scroll with the content. The footer is only visible when the `TabView` is displaying the sidebar.

The following example adds a link to contact support to the bottom of the sidebar content:

```
TabView {
    Tab("Home", systemImage: "house") {
        HomeView()
    }

    Tab("Alerts", systemImage: "bell") {
        AlertsView()
    }

    Tab("Browse", systemImage: "list.bullet") {
        MyBrowseView()
    }
}
.tabViewStyle(.sidebarAdaptable)
.tabViewSidebarFooter {
    ContactSupportLink()
}
```

