

- ClockKit
- CLKComplicationAppIntentWidgetMigrationConfiguration
-  init(kind:extensionBundleIdentifier:intent:localizedDisplayName:) 

Initializer

# init(kind:extensionBundleIdentifier:intent:localizedDisplayName:)

Creates an object that describes a watchOS complication that uses app intents in your WidgetKit extension.

watchOS 10.0+

``` source
init(
    kind: String,
    extensionBundleIdentifier: String,
    intent: Intent,
    localizedDisplayName: String
)
```

## Parameters 

`kind`  

A string that uniquely identifies a widget in your WidgetKit extension.

`extensionBundleIdentifier`  

The bundle identifier for your WidgetKit extension.

`intent`  

An intent that provides additional configuration information to your WidgetKit complication.

`localizedDisplayName`  

A localized name for the complication.

