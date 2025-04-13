

- PencilKit
- PKCanvasView
-  maximumSupportedContentVersion 

Instance Property

# maximumSupportedContentVersion

The maximum version of PencilKit to support.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+visionOS 1.0+

``` source
@MainActor
var maximumSupportedContentVersion: PKContentVersion { get set }
```

## Discussion

The default value is latest.

If you set this property to a value less than latest, the canvas view limits the edits that a person can make so they’re compatible with the version of PencilKit you specify.

If you set this property, also set maximumSupportedContentVersion on any PKToolPicker you use.

