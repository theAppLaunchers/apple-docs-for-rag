

- SwiftUI
-  TabView 

Structure

# TabView

A view that switches between multiple child views using interactive user interface elements.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 7.0+

``` source
struct TabView where SelectionValue : Hashable, Content : View
```

## Overview

To create a user interface with tabs, place Tabs in a `TabView`. On iOS, you can also use one of the badge modifiers, like badge(_:), to assign a badge to each of the tabs.

The following example creates a tab view with three tabs, each presenting a custom child view. The first tab has a numeric badge and the third has a string badge.

```
TabView {
    Tab("Received", systemImage: "tray.and.arrow.down.fill") {
        ReceivedView()
    }
    .badge(2)

    Tab("Sent", systemImage: "tray.and.arrow.up.fill") {
        SentView()
    }

    Tab("Account", systemImage: "person.crop.circle.fill") {
        AccountView()
    }
    .badge("!")
}
```

To programatically select different tabs, use the init(selection:content:) initializer. You can assign a selection value to each tab using a `Tab` initializer that takes a value. Each tab should have a unique selection value and all tabs should have the same selection value type. When people select a tab in the tab view, the tab view updates the selection binding to the value of the currently selected tab.

The following example creates a tab view that supports programatic selection and has 3 tabs.

```
TabView(selection: $selection) {
    Tab("Received", systemImage: "tray.and.arrow.down.fill", value: 0) {
        ReceivedView()
    }

    Tab("Sent", systemImage: "tray.and.arrow.up.fill", value: 1) {
        SentView()
    }

    Tab("Account", systemImage: "person.crop.circle.fill", value: 2) {
        AccountView()
    }
}
```

You can use the page style to display a tab view with multiple scrolling pages of content.

The following example uses a `ForEach` to create a scrolling tab view that shows the temperatures of various cities.

```
TabView {
    ForEach(cities) { city in
        TemperatureView(city)
    }
}
.tabViewStyle(.page)
```

### Using tab sections

The sidebarAdaptable style supports declaring a secondary tab hierarchy by grouping tabs with a TabSection.

On iPadOS, tab sections appear in both the sidebar and the tab bar. On iOS and the horizontally compact size class on iPadOS, secondary tabs appear in the tab bar. When secondary tabs appear in the tab bar, the section header doesn’t appear in the tab bar. Consider limiting the number of tabs on iOS and the iPadOS horizontal compact size class so all tabs fit in the tab bar.

The following example has 5 tabs, three of which are grouped within a TabSection.

```
TabView {
    Tab("Requests", systemImage: "paperplane") {
        RequestsView()
    }

    Tab("Account", systemImage: "person.crop.circle.fill") {
        AccountView()
    }

    TabSection("Messages") {
        Tab("Received", systemImage: "tray.and.arrow.down.fill") {
            ReceivedView()
        }

        Tab("Sent", systemImage: "tray.and.arrow.up.fill") {
            SentView()
        }

        Tab("Drafts", systemImage: "pencil") {
            DraftsView()
        }
    }
}
.tabViewStyle(.sidebarAdaptable)
```

### Changing tab structure between horizontal and regular size classes

The following example shows a `TabView` with 4 tabs in compact and 5 tabs in regular. In compact, one of the tabs is a ‘Browse’ tab that displays a custom list view. This list view allows navigating to the destinations that are contained within the ‘Library’ and ‘Playlists’ sections in the horizontally regular size class. The navigation path and the selection state are updated when the number of tabs changes.

```
struct BrowseTabExample: View {
    @Environment(\.horizontalSizeClass) var sizeClass

    @State var selection: MusicTab = .listenNow
    @State var browseTabPath: [MusicTab] = []
    @State var playlists = [Playlist("All Playlists"), Playlist("Running")]

    var body: some View {
            TabView(selection: $selection) {
                Tab("Listen Now", systemImage: "play.circle", value: .listenNow) {
                    ListenNowView()
                }

                Tab("Radio", systemImage: "dot.radiowaves.left.and.right", value: .radio) {
                    RadioView()
                }

                Tab("Search", systemImage: "magnifyingglass", value: .search) {
                    SearchDetailView()
                }

                Tab("Browse", systemImage: "list.bullet", value: .browse) {
                    LibraryView(path: $browseTabPath)
                }
                .hidden(sizeClass != .compact)

                TabSection("Library") {
                    Tab("Recently Added", systemImage: "clock", value: MusicTab.library(.recentlyAdded)) {
                        RecentlyAddedView()
                    }

                    Tab("Artists", systemImage: "music.mic", value: MusicTab.library(.artists)) {
                        ArtistsView()
                    }
                }
                .hidden(sizeClass == .compact)

                TabSection("Playlists") {
                    ForEach(playlists) { playlist in
                        Tab(playlist.name, image: playlist.imafe, value: MusicTab.playlists(playlist)) {
                            playlist.detailView()
                        }
                    }
                }
                .hidden(sizeClass == .compact)
            }
            .tabViewStyle(.sidebarAdaptable)
            .onChange(of: sizeClass, initial: true) { _, sizeClass in
                if sizeClass == .compact && selection.showInBrowseTab {
                    browseTabPath = [selection]
                    selection = .browse
                } else if sizeClass == .regular && selection == .browse {
                    selection = browseTabPath.last ?? .library(.recentlyAdded)
                }
            }
        }
    }
}

struct LibraryView: View {
    @Binding var path: [MusicTab]

    var body: some View {
        NavigationStack(path: $path) {
            List {
                ForEach(MusicLibraryTab.allCases, id: \.self) { tab in
                    NavigationLink(tab.rawValue, value: MusicTab.library(tab))
                }
                // Code to add playlists here
            }
            .navigationDestination(for: MusicTab.self) { tab in
                tab.detail()
            }
        }
    }
}
```

### Adding support for customization

You can allow people to customize the tabs in a `TabView` by using `sidebarAdaptable` style with the tabViewCustomization(_:) modifier. Customization allows people to drag tabs from the sidebar to the tab bar, hide tabs, and rearrange tabs in the sidebar.

All tabs and tab sections that support customization need to have a customization ID. You can mark a tab as being non-customizable by specifying a disabled behavior in all adaptable tab bar placements using customizationBehavior(_:for:).

On macOS, a default interaction is provided for reordering sections but not for controlling the visibility of individual tabs. A custom experience should be provided if desired by setting the visibility of the tab on the customization.

You can use `@AppStorage` or `@SceneStorage` to automatically persist any visibility or section order customizations a person makes.

The following example supports customizing all 4 tabs in the tab view and uses `@AppStorage` to persist the customizations a person makes.

```
@AppStorage
private var customization: TabViewCustomization

TabView {
    Tab("Home", systemImage: "house") {
        MyHomeView()
    }
    .customizationID("com.myApp.home")

    Tab("Reports", systemImage: "chart.bar") {
        MyReportsView()
    }
    .customizationID("com.myApp.reports")

    TabSection("Categories") {
        Tab("Climate", systemImage: "fan") {
            ClimateView()
        }
        .customizationID("com.myApp.climate")

        Tab("Lights", systemImage: "lightbulb") {
            LightsView()
        }
        .customizationID("com.myApp.lights")
    }
    .customizationID("com.myApp.browse")
}
.tabViewStyle(.sidebarAdaptable)
.tabViewCustomization($customization)
```

## Topics

### Creating a tab view

init(content:)

Creates a tab view that uses a builder to create its tabs.

init(selection:content:)

Creates a tab view that uses a builder to create and specify selection values for its tabs.

## Relationships

### Conforms To

- View

## See Also

### Presenting views in tabs

Enhancing your app’s content with tab navigation

Keep your app content front and center while providing quick access to navigation using the tab bar.

struct Tab

The content for a tab and the tab’s associated tab item in a tab view.

struct TabRole

A value that defines the purpose of the tab.

struct TabSection

A container that you can use to add hierarchy within a tab view.

func tabViewStyle&lt;S>(S) -> some View

Sets the style for the tab view within the current environment.

