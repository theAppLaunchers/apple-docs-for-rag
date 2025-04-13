

- App Intents
- AssistantSchemas
- AssistantSchemas.IntentSchema
-  setWarmth 

Instance Property

# setWarmth

The app intent conforms to the schema for setting the warmth of an asset.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+watchOS 9.0+

``` source
var setWarmth: some AssistantSchemas.Intent { get }
```

## Overview

To integrate your app’s functionality with Siri and Apple Intelligence, you use Swift macros that generate additional properties and add protocol conformance for your app intent implementation.

For more information about the `.photos` app intent domain, see Making photo and video actions available to Siri and Apple Intelligence. For general information about app intent domains, see Integrating actions with Siri and Apple Intelligence.

The following example shows an app intent that conforms to the `.photos.setWarmth` schema:

```
@AssistantIntent(schema: .photos.setWarmth)
struct SetMediaWarmthIntent: AppIntent {
    @Parameter
    var target: PhotoEntity

    @Parameter
    var value: Double?

    func perform() async throws -> some IntentResult {
        .result()
    }
}
```

