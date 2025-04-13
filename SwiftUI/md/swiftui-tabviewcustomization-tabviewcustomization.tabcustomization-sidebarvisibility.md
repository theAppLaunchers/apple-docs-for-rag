

- SwiftUI
- TabViewCustomization
- TabViewCustomization.TabCustomization
-  sidebarVisibility 

Instance Property

# sidebarVisibility

The visibility of the tab in the sidebar.

iOS 18.4+iPadOS 18.4+Mac Catalyst 18.4+macOS 15.4+visionOS 2.4+

``` source
var sidebarVisibility: Visibility { get set }
```

## Discussion

Visibility can be set imperatively by subscripting with the tab’s id:

```
customization[tab: "com.myApp.alerts"].sidebarVisibility = .hidden
```

You can change the default visibility by using `TabContent/defaultVisibility(_:for)` with a `AdaptableTabBarPlacement.sidebar` placement.

```
Tab("Alerts", systemImage: "bell", value: .alerts) {
    AlertsView()
}
.customizationID("com.myApp.alerts")
.defaultVisibility(.hidden, for: .sidebar)
```

If the ID isn’t associated with a tab or the tab has not been customized, a default value of `.automatic` is returned.

