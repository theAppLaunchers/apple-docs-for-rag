

- WidgetKit
-  AccessoryWidgetGroup 

Structure

# AccessoryWidgetGroup

A view type that has a label at the top and three content views masked with a circle or rounded square.

watchOS 11.0+

``` source
@MainActor @preconcurrency
struct AccessoryWidgetGroup where Label : View, Content : View
```

## Overview

You can use this view on `.accessoryRectangular` family widgets on watchOS to lay out three content views horizontally inside of a rectangular widget.

Example usage:

```
struct WeatherGroupView: View {
   var entry: Provider.Entry

   var body: some View {
       AccessoryWidgetGroup("Weather", systemImage: "cloud.sun.fill") {
           TemperatureWidgetView(entry.temperature)
           ConditionsWidgetView(entry.conditions)
           UVIndexWidgetView(entry.UVIndex)
       }
       .accessoryWidgetGroupStyle(.circular)
   }
}
```

The above example creates an `.accessoryRectangular` widget that has a `SwiftUI.Label` as its label and has three content views: temperature, conditions, and UVIndex; all of which are circular. If the developers provide fewer than three views, the AccessoryWidgetGroup will insert however many custom empty view(s) to ensure that three views exist in the `content`.

You can change the shape with which the content views are masked using the `.accessoryWidgetGroupStyle(_:)` view modifier.

## Topics

### Initializers

init(some StringProtocol, content: () -> Content)

Creates an `AccessoryWidgetGroup` that generates its label from a string.

init(LocalizedStringKey, content: () -> Content)

Creates an `AccessoryWidgetGroup` that generates its label from a localized string key.

init(LocalizedStringKey, image: ImageResource, content: () -> Content)

Creates an `AccessoryWidgetGroup` that generates its label from a localized string key and image resource.

init(some StringProtocol, image: ImageResource, content: () -> Content)

Creates an `AccessoryWidgetGroup` that generates its label from a string and image resource.

init(LocalizedStringKey, systemImage: String, content: () -> Content)

Creates an `AccessoryWidgetGroup` that generates its label from a localized string key and a system image name.

init(some StringProtocol, systemImage: String, content: () -> Content)

Creates an `AccessoryWidgetGroup` that generates its label from a string and system image name.

init(label: () -> Label, content: () -> Content)

Creates an AccessoryWidgetGroup composed of a label and three circular or rounded square contents with equal spacing and vertical alignment.

## Relationships

### Conforms To

- View

