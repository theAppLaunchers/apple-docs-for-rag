

- App Intents
- OpenURLIntent
-  isDiscoverable 

Type Property

# isDiscoverable

A boolean value that determines whether system features such as Shortcuts and Spotlight can discover this app intent.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+tvOS 17.0+visionOS 1.0+watchOS 10.0+

``` source
static var isDiscoverable: Bool { get }
```

## Discussion

App Intents must be discoverable to support App Shortcuts. If your app intent isn’t discoverable, people can use it only when it’s directly connected by a button in a SwiftUI app or a widget.

This property is `true` by default.

