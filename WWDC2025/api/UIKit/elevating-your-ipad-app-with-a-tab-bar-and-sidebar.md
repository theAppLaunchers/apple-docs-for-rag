*   [UIKit](/documentation/uikit)
*   [App and environment](/documentation/uikit/app-and-environment)
*   Elevating your iPad app with a tab bar and sidebar

Article

# Elevating your iPad app with a tab bar and sidebar

Provide a compact, ergonomic tab bar for quick access to key parts of your app, and a sidebar for in-depth navigation.

## [Overview](/documentation/UIKit/elevating-your-ipad-app-with-a-tab-bar-and-sidebar#overview)

In iPadOS 18 and later, the position of the tab bar moves from the bottom of the screen to float over your content at the top. This compact appearance gives you more space for your app’s content. Additionally, because it shares space with the navigation bar, it places your tabs closer to your app’s other controls.

![An illustration of an iPad that shows the placement of the floating tab bar at the top of the screen.](https://docs-assets.developer.apple.com/published/fc0acda64bf43bcf4db9770a65b6dfe3/media-4445108%402x.png)

iPadOS apps automatically receive the new tab bar appearance when you compile them for iPadOS 18 and later.

SwiftUI equivalent

For information about adopting the new tab bar appearance in SwiftUI, read [Enhancing your app’s content with tab navigation](/documentation/SwiftUI/Enhancing-your-app-content-with-tab-navigation).

### [Create a tab bar](/documentation/UIKit/elevating-your-ipad-app-with-a-tab-bar-and-sidebar#Create-a-tab-bar)

iPadOS 18 also introduces new API for creating tab bars. Create a [`UITabBarController`](/documentation/uikit/uitabbarcontroller) and assign an array of [`UITab`](/documentation/uikit/uitab) objects to its [`tabs`](/documentation/uikit/uitabbarcontroller/tabs) property. To create a tab, call [`init(title:image:identifier:viewControllerProvider:)`](/documentation/uikit/uitab/init\(title:image:identifier:viewcontrollerprovider:\)). In the closure, return the view controller your app presents when someone selects the tab. If you use SF Symbols for your tab’s image, be sure to select the outline variant. The system automatically selects the correct variant (outline or filled) based on the context. Additionally, you can change a tab’s properties, such as [`title`](/documentation/uikit/uitab/title) or [`image`](/documentation/uikit/uitab/image), at runtime, and the system automatically updates its appearance.

```swift

```swift
// Create the tab bar controller.
```swift
```swift
let tabBarController = UITabBarController()
```
```
// Assign an array of tabs.
tabBarController.tabs = [
   UITab(title: "First",
         image: UIImage(systemName: "1.circle"),
         identifier: "First Tab") { _ in
             // Return the view controller that the tab displays.
             MyFirstViewController()
         },
   
   UITab(title: "Second",
         image: UIImage(systemName: "2.circle"),
         identifier: "Second Tab") { _ in
             // Return the view controller that the tab displays.
             MySecondViewController()
         },
   
   UITab(title: "Third",
         image: UIImage(systemName: "3.circle"),
         identifier: "Third Tab") { _ in
             // Return the view controller that the tab displays.
             MyThirdViewController()
         }
]
```

```

To add a search tab, create a [`UISearchTab`](/documentation/uikit/uisearchtab) instance and add it to the tabs array.

```

```
// Create a search tab.
UISearchTab { _ in 
    // Return the view controller that the tab displays.
    UINavigationController(
        rootViewController: MySearchViewController()
    )
}
```

```

![An illustration of an iPad that shows the position of the first, second, and third tabs at the top of the screen.](https://docs-assets.developer.apple.com/published/66fb92382026cbc7d6e7fb097e06cbef/media-4445106%402x.png)

The new iPad tab bar supports an unlimited number of items. If there isn’t enough room to display all the tabs, the system collapses any tabs that can’t fit onscreen, and lets people scroll through them. However, consider limiting your tabs to just those that fit in the tab bar. This ensures that people can access key parts of your app with one tap.

### [Integrate the tab bar and sidebar](/documentation/UIKit/elevating-your-ipad-app-with-a-tab-bar-and-sidebar#Integrate-the-tab-bar-and-sidebar)

Although both tab bars and sidebars play a similar navigation role in iPadOS apps, they have different strengths. A tab bar is always available and represents the key parts of your app. A sidebar provides a richer collection of possible destinations; however, people typically need to navigate back to the sidebar to select a different option.

If your app contains a rich hierarchy of views, you can create an array of tab items that the system displays as either a tab bar or a sidebar. This combination provides the best features of both navigation styles. When displaying as a tab bar, people have quick access to the most critical sections of your app. When displaying as a sidebar, they can see the full range and depth of your app.

![An illustration of two iPads side by side. The first iPad shows the sidebar on the left of the screen in landscape orientation. The second iPad shows the tab bar at the top of the screen in portrait orientation.](https://docs-assets.developer.apple.com/published/bb61d76b1c0cea3251da84d1bc2f1cdf/media-4445103%402x.png)

Use the new [`UITab`](/documentation/uikit/uitab) and [`UITabGroup`](/documentation/uikit/uitabgroup) classes to create a hierarchy of tabs. If the tabs array contains at least one tab group, the system automatically displays the tabs as both a tab bar and a sidebar. Otherwise, it only displays the array as a tab bar. You can also explicitly define how the system displays your tabs by setting the [`UITabBarController`](/documentation/uikit/uitabbarcontroller) object’s [`mode`](/documentation/uikit/uitabbarcontroller/mode-swift.property) property.

```swift

```swift
// Enable the sidebar.
tabBarController.mode = .tabSidebar
// Get the sidebar.
```swift
```swift
let sidebar = tabBarController.sidebar
```
```
// Show the sidebar.
sidebar.isHidden = false
```

```

By default, the system presents the sidebar in landscape orientation and hides it in portrait orientation; however, people can toggle between the tab bar and sidebar in either orientation. You can also programmatically show and hide the sidebar by setting its [`isHidden`](/documentation/uikit/uitabbarcontroller/sidebar-swift.class/ishidden) property.

### [Build a hierarchy of items for the sidebar](/documentation/UIKit/elevating-your-ipad-app-with-a-tab-bar-and-sidebar#Build-a-hierarchy-of-items-for-the-sidebar)

You can use [`UITabGroup`](/documentation/uikit/uitabgroup) to define a section of items in the sidebar. Provide an array of tabs for the section’s content and a view controller to display when someone selects the section from the tab bar.

```swift
```swift
```swift
```swift
```swift
```swift
let sectionOne = UITabGroup(
```
```
    title: "Section 1",
    image: UIImage(systemName: "1.square.fill"),
    identifier: "Section one",
    children:
        [
            UITab(
                title: "Subitem A",
                image: UIImage(systemName: "a.circle"),
                identifier: "Section 1, item A"
            ) { _ in
                MyFirstSubitemTabViewController()
            },
            
            UITab(
                title: "Subitem B",
                image: UIImage(systemName: "b.circle"),
                identifier: "Section 1, item b"
            ) { _ in
                MySecondSubitemTabViewController()
            },
            
            UITab(
                title: "Subitem C",
                image: UIImage(systemName: "c.circle"),
                identifier: "Section 1, item C"
            ) { _ in
                MyThirdSubitemTabViewController()
            },
        ]) { _ in
            // Return a view controller that the system displays when someone selects the section in the tab bar.
            MySectionViewController()
        }
```
```
```
```

The tab bar displays a tab group as a single tab item, and the sidebar displays it as a section that contains subitems. The sidebar displays top-level tab items first, followed by the sections.

![An illustration of an iPad in landscape orientation that shows the sidebar displaying a hierarchy of tabs. The top-level tabs appear first, followed by the tab groups.](https://docs-assets.developer.apple.com/published/3067e4834387868745dde6e7df887d63/media-4445107%402x.png)

You can nest a [`UITabGroup`](/documentation/uikit/uitabgroup) inside another [`UITabGroup`](/documentation/uikit/uitabgroup) to create a deeper hierarchy in the sidebar; however, consider limiting your app to two, or at most three, layers. Also, you can dynamically change a tab group’s content at runtime by modifying its [`children`](/documentation/uikit/uitabgroup/children) property.

### [Add actions to the sidebar](/documentation/UIKit/elevating-your-ipad-app-with-a-tab-bar-and-sidebar#Add-actions-to-the-sidebar)

You can add actions to the sidebar by setting a tab group’s [`sidebarActions`](/documentation/uikit/uitabgroup/sidebaractions) property. These actions function like buttons that you place inside the tab group.

```swift

```swift
// Create the action.
```swift
```swift
let refreshAction = UIAction(title: "Refresh", image: UIImage(systemName: "arrow.clockwise")) { _ in
```
```
    myAction()
}
// Assign the action.
sectionOne.sidebarActions = [refreshAction]
```

```

To support swipe actions or context menus, assign a delegate to your sidebar that adopts the [`UITabBarController.Sidebar.Delegate`](/documentation/uikit/uitabbarcontroller/sidebar-swift.class/delegate-swift.protocol) protocol, and implement the following optional methods:

*   [`tabBarController(_:sidebar:leadingSwipeActionsConfigurationFor:)`](/documentation/uikit/uitabbarcontroller/sidebar-swift.class/delegate-swift.protocol/tabbarcontroller\(_:sidebar:leadingswipeactionsconfigurationfor:\))
    
*   [`tabBarController(_:sidebar:trailingSwipeActionsConfigurationFor:)`](/documentation/uikit/uitabbarcontroller/sidebar-swift.class/delegate-swift.protocol/tabbarcontroller\(_:sidebar:trailingswipeactionsconfigurationfor:\))
    
*   [`tabBarController(_:sidebar:contextMenuConfigurationFor:)`](/documentation/uikit/uitabbarcontroller/sidebar-swift.class/delegate-swift.protocol/tabbarcontroller\(_:sidebar:contextmenuconfigurationfor:\))
    

To support drag-and-drop operations, assign a delegate to your tab bar that adopts the [`UITabBarControllerDelegate`](/documentation/uikit/uitabbarcontrollerdelegate) protocol, and implement the [`tabBarController(_:tab:operationForAcceptingItemsFrom:)`](/documentation/uikit/uitabbarcontrollerdelegate/tabbarcontroller\(_:tab:operationforacceptingitemsfrom:\)) and [`tabBarController(_:tab:acceptItemsFrom:)`](/documentation/uikit/uitabbarcontrollerdelegate/tabbarcontroller\(_:tab:acceptitemsfrom:\)) methods.

### [Enable customization](/documentation/UIKit/elevating-your-ipad-app-with-a-tab-bar-and-sidebar#Enable-customization)

With the new tab bar and sidebar, people can customize the content in both. The system provides a button to put the bars into edit mode. While editing, people can:

*   Drag items from the sidebar to the tab bar to add them to the tab bar.
    
*   Drag items from the tab bar to remove them from the tab bar.
    
*   Drag items to reorder them in the tab bar.
    
*   Drag items to reorder them inside their tab group.
    
*   Uncheck items in the sidebar to hide them. This also removes them from the tab bar.
    

The system automatically persists any customizations that someone makes to the bars. You can implement the [`tabBarController(_:displayOrderDidChangeFor:)`](/documentation/uikit/uitabbarcontrollerdelegate/tabbarcontroller\(_:displayorderdidchangefor:\)) and [`tabBarController(_:visibilityDidChangeFor:)`](/documentation/uikit/uitabbarcontrollerdelegate/tabbarcontroller\(_:visibilitydidchangefor:\)) delegate methods to receive notifications about the changes.

![An illustration of an iPad in landscape orientation that shows the sidebar and tab bar in edit mode.](https://docs-assets.developer.apple.com/published/c4c8ad7d5cfdc2808cded2caea9e3160/media-4445104%402x.png)

By default, only the top-level tabs appear in the tab bar. People can add or remove any tab in the sidebar, but can’t hide or reorder the items in it.

To control which items appear in the tab bar, and how people can customize them, set the [`UITab`](/documentation/uikit/uitab) object’s [`preferredPlacement`](/documentation/uikit/uitab/preferredplacement) property. Conceptually, you can think of the tab bar as having three different regions:

*   Fixed tabs appear on the leading edge of the tab bar.
    
*   Default, optional, and movable tabs appear after the fixed tabs.
    
*   Pinned tabs are always visible on the trailing edge, and only show the tab’s image.
    

When possible, make tabs customizable so that people can choose which ones to place in the tab bar. If you have any tabs that are central to your app, consider making them fixed tabs, so that people can’t remove or move them. Use pinned tabs for prominent items, like search. Also, because pinned tabs only display the tab icon, be sure to select an image that people recognize and can easily understand.

![An illustration of an iPad in landscape orientation that shows the fixed, optional, pinned, and movable tabs in the tab bar and sidebar.](https://docs-assets.developer.apple.com/published/81e6a1c64b1dbe14dab3c85e36c98a24/media-4445105%402x.png)

To create an item that appears in the sidebar, but that people can’t add to the tab bar, set the [`preferredPlacement`](/documentation/uikit/uitab/preferredplacement) property to [`UITab.Placement.sidebarOnly`](/documentation/uikit/uitab/placement/sidebaronly). To create an item that people can add to or remove from the sidebar, set its [`allowsHiding`](/documentation/uikit/uitab/allowshiding) property to [`true`](/documentation/swift/true). If someone removes an item from the sidebar, the system also removes it from the tab bar.

```swift

```swift
// Create the tab.
```swift
```swift
var customizeableItem = UITab(
```
```
        title: "Optional",
        image: UIImage(systemName: "questionmark.app"),
        identifier: "Optional Item"
) { _ in
    MyOptionalViewController()
}
// Let people add and remove this item in the sidebar.
customizeableItem.allowsHiding = true
// Set the item as hidden in the sidebar by default.
customizeableItem.isHiddenByDefault = true
```

```

To let people reorganize items within a tab group, set the group’s [`allowsReordering`](/documentation/uikit/uitabgroup/allowsreordering) property to [`true`](/documentation/swift/true).

```

```
sectionOne.allowsReordering = true
```

```

You can also programmatically set the order of items in a tab group using its [`displayOrderIdentifiers`](/documentation/uikit/uitabgroup/displayorderidentifiers) property. By default, the system sets the tab group’s order based on its [`children`](/documentation/uikit/uitabgroup/children) property.

Important

When someone customizes the tab bar or sidebar, the system persists those changes. The next time your app launches, it sets each tab’s [`isHidden`](/documentation/uikit/uitab/ishidden) and [`displayOrderIdentifiers`](/documentation/uikit/uitabgroup/displayorderidentifiers) properties to the customized values. The system assigns these values when it adds the tab to the [`UITabBarController`](/documentation/uikit/uitabbarcontroller). If your app programmatically sets the [`isHidden`](/documentation/uikit/uitab/ishidden) or [`displayOrderIdentifiers`](/documentation/uikit/uitabgroup/displayorderidentifiers) properties before adding the tabs, the customized values override the values your app assigns. If, however, you change the values after adding the tabs, your values override the customizations.

### [Use the tab bar and sidebar on other platforms](/documentation/UIKit/elevating-your-ipad-app-with-a-tab-bar-and-sidebar#Use-the-tab-bar-and-sidebar-on-other-platforms)

The new [`UITab`](/documentation/uikit/uitab) API is also available in iOS 18, Mac Catalyst 18, tvOS 18, and visionOS 2, and later. Consider using this API to create tab bars on all UIKit-based projects.

The new tab bar and sidebar only appear on iPad. On iPhone and Apple TV, the system displays the platform’s regular tab bar. For Mac Catalyst, it displays a tab bar if the tab bar controller’s [`mode`](/documentation/uikit/uitabbarcontroller/mode-swift.property) property is [`UITabBarController.Mode.tabBar`](/documentation/uikit/uitabbarcontroller/mode-swift.enum/tabbar), and a sidebar if it’s [`UITabBarController.Mode.tabSidebar`](/documentation/uikit/uitabbarcontroller/mode-swift.enum/tabsidebar).

In visionOS, the system displays the platform’s regular tabs, but a [`UITabGroup`](/documentation/uikit/uitabgroup) can display a sidebar when it displays the group’s view controller.

## [See Also](/documentation/UIKit/elevating-your-ipad-app-with-a-tab-bar-and-sidebar#see-also)

### [iPad](/documentation/UIKit/elevating-your-ipad-app-with-a-tab-bar-and-sidebar#iPad)

[

Building a desktop-class iPad app](/documentation/uikit/building-a-desktop-class-ipad-app)

Optimize your iPad app’s user experience by adopting desktop-class enhancements for multitasking with Stage Manager, document interactions, text editing, search, and more.

[

Supporting desktop-class features in your iPad app](/documentation/uikit/supporting-desktop-class-features-in-your-ipad-app)

Enhance your iPad app by adding desktop-class features and document support.

[

API Reference

Multitasking on iPad](/documentation/uikit/multitasking-on-ipad)

Implement multitasking APIs to seamlessly integrate your app with iPadOS.