

- Foundation
- NSExtensionContext
-  intent 

Instance Property

# intent

Metadata for populating your share extensions interface.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.1+visionOS 1.0+watchOS 6.0+

``` source
var intent: INIntent? { get }
```

## Mentioned in 

Supporting suggestions in your app’s share extension

## Discussion

When the user selects an app from the list of suggested apps in iOS’s share sheet, this property contains metadata that you can use to populate your share extensions interface. The source for the metadata is the doc://com.apple.documentation/documentation/sirikit/insendmessageintent of your messaging app.

This property is `nil` if your app’s share extension wasn’t launched from the list of suggested apps.

Note

To learn more about adding a share extension to the list of suggested apps, read Supporting suggestions in your app’s share extension.

