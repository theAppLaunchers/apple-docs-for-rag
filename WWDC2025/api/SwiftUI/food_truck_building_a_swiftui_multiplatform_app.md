*   [SwiftUI](/documentation/swiftui)
*   Food Truck: Building a SwiftUI multiplatform app

Sample Code

# Food Truck: Building a SwiftUI multiplatform app

Create a single codebase and app target for Mac, iPad, and iPhone.

[Download](https://docs-assets.developer.apple.com/published/ea7c0bd405/FoodTruckBuildingASwiftUIMultiplatformApp.zip)

iOS 16.4+iPadOS 16.4+macOS 13.3+Xcode 14.3+

## [Overview](/documentation/swiftui/food_truck_building_a_swiftui_multiplatform_app#overview)

Using the Food Truck app, someone who operates a food truck can keep track of orders, discover the most-popular menu items, and check the weather at their destination. The sample implements the new [`NavigationSplitView`](/documentation/swiftui/navigationsplitview) to manage the app’s views, [Layout modifiers](/documentation/swiftui/view-layout) to show the main interface and pending orders, [Swift Charts](/documentation/charts) to show trends, and [`WeatherService`](/documentation/weatherkit/weatherservice) to get weather data. Food Truck also implements Live Activities to show the remaining order preparation time with [ActivityKit](/documentation/activitykit) on the lock screen, and with [`DynamicIsland`](/documentation/widgetkit/dynamicisland) on the home screen.

You can access the source code for this sample on [GitHub](https://github.com/apple/sample-food-truck).

Note

This sample code project is associated with WWDC22 session [110492: State of the Union](https://developer.apple.com/wwdc22/110492/).

The Food Truck sample project contains two types of app targets:

*   Simple app target you can build using [personal team](https://help.apple.com/xcode/mac/11.4/#/dev17411c009) signing. This app runs in Simulator, and only requires a standard Apple ID to install on a device. It includes in-app purchase, and a widget extension that enable users to add a widget to their iOS Home Screen or the macOS Notification Center.
    
*   Full-featured Food Truck All app target. The full app runs in Simulator, and on devices with an Apple Developer membership. It also allows you to create and sign in with passkeys.
    

### [Configure the sample code project](/documentation/swiftui/food_truck_building_a_swiftui_multiplatform_app#4143584)

To configure the Food Truck app without an Apple Developer account, follow these steps:

1.  In the Food Truck target’s Signing & Capabilities panes click Add Account, and log in with your Apple ID.
    
2.  Chose Your Name (Personal Team) from the team menu for the Food Truck and Widgets targets.
    
3.  Build and run your app.
    
4.  On iOS and iPadOS devices navigate to Settings > General > VPN & Device Management and trust your developer certificate.
    

To configure the Food Truck All app to run on your devices, follow these steps:

1.  Open the sample with Xcode 14.3 or later.
    
2.  Select the top-level Food Truck project.
    
3.  For all targets, choose your team from the Team menu in the Signing & Capabilities pane, so Xcode can automatically manage your provisioning profile.
    
4.  Add the Associated Domains capability, and specify your domain with the `webcredentials` service. For more information about the `webcredentials` service, see [`Associated Domains Entitlement`](/documentation/bundleresources/entitlements/com.apple.developer.associated-domains).
    
5.  Ensure an `apple-app-site-association` (AASA) file is present on your domain, in the `.well-known` directory, and it contains an entry for this app’s App ID for the `webcredentials` service. For more information about the `apple-app-site-association` file, see [Supporting associated domains](/documentation/xcode/supporting-associated-domains).
    
6.  In the `AccountManager.swift` file, replace all occurrences of `example.com` with the name of your domain.
    

Note

To use the weather forecast feature in the sample, you need to perform additional steps to configure WeatherKit, as described in the Configure the project for WeatherKit section below, or the sample will detect an error and use static data included in the project.

### [Create a multiplatform app](/documentation/swiftui/food_truck_building_a_swiftui_multiplatform_app#4143585)

Food Truck is a multiplatform app, and there are no separate targets to run on macOS or iOS. Instead, there is only one app target that builds for macOS, iPadOS, and iOS.

### [Define a default navigation destination](/documentation/swiftui/food_truck_building_a_swiftui_multiplatform_app#4143586)

The sample’s navigation interface consists of a [`NavigationSplitView`](/documentation/swiftui/navigationsplitview) with a `Sidebar` view, and a [`NavigationStack`](/documentation/swiftui/navigationstack):

```

```
NavigationSplitView {
    Sidebar(selection: $selection)
} detail: {
    NavigationStack(path: $path) {
        DetailColumn(selection: $selection, model: model)
    }
}
```

```

At app launch, the sample presents the `TruckView` as the default view. The `Panel` enum encodes the views the user can select in the sidebar, and hence appear in the detail view. The value corresponding to `TruckView` is `.truck`, and the app sets this to be the default selection.

```swift

```swift
@State private var selection: Panel? = Panel.truck
```

```

### [Construct a dynamic layout](/documentation/swiftui/food_truck_building_a_swiftui_multiplatform_app#4143587)

In the Truck view, the New Orders panel shows the five most-recent orders, and each order shows a `DonutStackView`, which is a diagonal stack of donut thumbnails. The [Layout modifiers](/documentation/swiftui/view-layout) protocol allows the app to define a `DiagonalDonutStackLayout` that arranges the donut thumbnails into the diagonal layout. The layout’s [`placeSubviews(in:proposal:subviews:cache:)`](/documentation/swiftui/layout/placesubviews\(in:proposal:subviews:cache:\)) implementation calculates the donuts’ positions.

```swift

```swift
for index in subviews.indices {
    switch (index, subviews.count) {
    case (_, 1):
        subviews[index].place(
            at: center,
            anchor: .center,
            proposal: ProposedViewSize(size)
        )
        
    case (_, 2):
        let direction = index == 0 ? -1.0 : 1.0
        let offsetX = minBound * direction * 0.15
        let offsetY = minBound * direction * 0.20
        subviews[index].place(
            at: CGPoint(x: center.x + offsetX, y: center.y + offsetY),
            anchor: .center,
            proposal: ProposedViewSize(CGSize(width: size.width * 0.7, height: size.height * 0.7))
        )
    case (1, 3):
        subviews[index].place(
            at: center,
            anchor: .center,
            proposal: ProposedViewSize(CGSize(width: size.width * 0.65, height: size.height * 0.65))
        )
        
    case (_, 3):
        let direction = index == 0 ? -1.0 : 1.0
        let offsetX = minBound * direction * 0.15
        let offsetY = minBound * direction * 0.23
        subviews[index].place(
            at: CGPoint(x: center.x + offsetX, y: center.y + offsetY),
            anchor: .center,
            proposal: ProposedViewSize(CGSize(width: size.width * 0.7, height: size.height * 0.65))
        )
```

```

### [Display a chart of popular items](/documentation/swiftui/food_truck_building_a_swiftui_multiplatform_app#4143588)

The sample contains several charts. The most popular items are shown on the `TopFiveDonutsView`. This chart is implemented in `TopDonutSalesChart`, which uses a [`BarMark`](/documentation/charts/barmark) to construct a bar chart.

```

```
Chart {
    ForEach(sortedSales) { sale in
        BarMark(
            x: .value("Donut", sale.donut.name),
            y: .value("Sales", sale.sales)
        )
        .cornerRadius(6, style: .continuous)
        .foregroundStyle(.linearGradient(colors: [Color("BarBottomColor"), .accentColor], startPoint: .bottom, endPoint: .top))
        .annotation(position: .top, alignment: .top) {
            Text(sale.sales.formatted())
                .padding(.vertical, 4)
                .padding(.horizontal, 8)
                .background(.quaternary.opacity(0.5), in: Capsule())
                .background(in: Capsule())
                .font(.caption)
        }
    }
}
```

```

The _x_ axis of the chart shows labels with the names and thumbnails of the items that correspond to each data point.

```swift

```swift
.chartXAxis {
    AxisMarks { value in
        AxisValueLabel {
            let donut = donutFromAxisValue(for: value)
            VStack {
                DonutView(donut: donut)
                    .frame(height: 35)
                    
                Text(donut.name)
                    .lineLimit(2, reservesSpace: true)
                    .multilineTextAlignment(.center)
            }
            .frame(idealWidth: 80)
            .padding(.horizontal, 4)
            
        }
    }
}
```

```

### [Obtain a weather forecast](/documentation/swiftui/food_truck_building_a_swiftui_multiplatform_app#4143589)

The app shows a forecasted temperature graph in the Forecast panel in the Truck view. The app obtains this data from the [WeatherKit](/documentation/weatherkit) framework.

```swift

```swift
.task(id: city.id) {
    for parkingSpot in city.parkingSpots {
        do {
            let weather = try await WeatherService.shared.weather(for: parkingSpot.location)
            condition = weather.currentWeather.condition
            willRainSoon = weather.minuteForecast?.contains(where: { $0.precipitationChance >= 0.3 })
            cloudCover = weather.currentWeather.cloudCover
            temperature = weather.currentWeather.temperature
            symbolName = weather.currentWeather.symbolName
            
            let attribution = try await WeatherService.shared.attribution
            attributionLink = attribution.legalPageURL
            attributionLogo = colorScheme == .light ? attribution.combinedMarkLightURL : attribution.combinedMarkDarkURL
            
            if willRainSoon == false {
                spot = parkingSpot
                break
            }
        } catch {
            print("Could not gather weather information...", error.localizedDescription)
            condition = .clear
            willRainSoon = false
            cloudCover = 0.15
        }
    }
}
```

```

### [Configure the project for WeatherKit](/documentation/swiftui/food_truck_building_a_swiftui_multiplatform_app#4143590)

The data from the [`WeatherService`](/documentation/weatherkit/weatherservice) instance in WeatherKit requires additional configuration for the Food Truck All target. If you don’t configure WeatherKit, the sample will detect an error and use static data in the project instead.

1.  Create a unique App ID on the [Provisioning Portal](https://developer.apple.com/account/resources/certificates/list), and select the WeatherKit service on the App Services tab.
    
2.  In Xcode, for the Food Truck All target on the Signing & Capabilities tab, change the bundle ID to be the same as the App ID from step 1, and add the WeatherKit capability.
    
3.  For the Widgets target on the Signing & Capabilities tab, change the bundle ID to make the part before `.Widgets` the same as the bundle ID for the Food Truck All target.
    
4.  Wait 30 minutes while the service registers your app’s bundle ID.
    
5.  Build and run the Food Truck All target.
    

### [Track preparation time with Live Activity](/documentation/swiftui/food_truck_building_a_swiftui_multiplatform_app#4143591)

The app allows the food truck operator to keep track of order preparation time, which is guaranteed to be 60 seconds or less. To facilitate this, the app implements a toolbar button on the order details screen for orders with `placed` status. Tapping this button changes the order status to `preparing`, and creates an [`Activity`](/documentation/activitykit/activity) instance to start a Live Activity, which shows the countdown timer and order details on an iPhone lock screen.

```swift
```swift
```swift
```swift
```swift
```swift
```swift
let timerSeconds = 60
```
```
```swift
```swift
let activityAttributes = TruckActivityAttributes(
```
```
    orderID: String(order.id.dropFirst(6)),
    order: order.donuts.map(\.id),
    sales: order.sales,
    activityName: "Order preparation activity."
)
```swift
```swift
let future = Date(timeIntervalSinceNow: Double(timerSeconds))
```
```
```swift
```swift
let initialContentState = TruckActivityAttributes.ContentState(timerRange: Date.now...future)
```
```
```swift
```swift
let activityContent = ActivityContent(state: initialContentState, staleDate: Calendar.current.date(byAdding: .minute, value: 2, to: Date())!)
```
```
do {
    let myActivity = try Activity<TruckActivityAttributes>.request(attributes: activityAttributes, content: activityContent,
        pushType: nil)
    print(" Requested MyActivity live activity. ID: \(myActivity.id)")
    postNotification()
} catch let error {
    print("Error requesting live activity: \(error.localizedDescription)")
}
```
```
```
```
```

The app also implements [`DynamicIsland`](/documentation/widgetkit/dynamicisland) to show the same information as on the lock screen in the Dynamic Island on iPhone 14 Pro devices.

```

```
DynamicIsland {
    DynamicIslandExpandedRegion(.leading) {
        ExpandedLeadingView()
    }
    DynamicIslandExpandedRegion(.trailing, priority: 1) {
        ExpandedTrailingView(orderNumber: context.attributes.orderID, timerInterval: context.state.timerRange)
            .dynamicIsland(verticalPlacement: .belowIfTooWide)
    }
} compactLeading: {
    Image("IslandCompactIcon")
        .padding(4)
        .background(.indigo.gradient, in: ContainerRelativeShape())
       
} compactTrailing: {
    Text(timerInterval: context.state.timerRange, countsDown: true)
        .monospacedDigit()
        .foregroundColor(Color("LightIndigo"))
        .frame(width: 40)
} minimal: {
    Image("IslandCompactIcon")
        .padding(4)
        .background(.indigo.gradient, in: ContainerRelativeShape())
}
.contentMargins(.trailing, 32, for: .expanded)
.contentMargins([.leading, .top, .bottom], 6, for: .compactLeading)
.contentMargins(.all, 6, for: .minimal)
.widgetURL(URL(string: "foodtruck://order/\(context.attributes.orderID)"))
```

```

Tapping the same button again changes the status to `complete`, and ends the Live Activity. This removes the Live Activity from the lock screen and from the Dynamic Island.

```

```
Task {
    for activity in Activity<TruckActivityAttributes>.activities {
        // Check if this is the activity associated with this order.
        if activity.attributes.orderID == String(order.id.dropFirst(6)) {
            await activity.end(nil, dismissalPolicy: .immediate)
        }
    }
}
```

```