

- ProximityReader
-  ProximityReaderDiscovery 

Class

# ProximityReaderDiscovery

An object that presents a UI with information about how to use Tap to Pay on iPhone.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+visionOS 2.0+

``` source
final class ProximityReaderDiscovery
```

## Overview

Use a ProximityReaderDiscovery object to educate people on how to read contactless credentials with their iPhone. When building a reader interface in your app, include controls to display help information. When a person taps those controls, use this type to present a view controller with information about how to use a particular feature. The system manages the presented view controller, displaying materials to teach people how the system works.

Create a ProximityReaderDiscovery object in response to requests for help from your app’s interface. Fetch a relevant help topic and present that topic using the presentContent(_:from:) method, as shown in the following example. Present the topic displays a new view controller with information about how to use the relevant features. This view controller remains visible until the person dismisses it, at which point control returns to your app’s current view controller.

```
let proximityReaderDiscovery = ProximityReaderDiscovery()

Task {
    do {
        let content = try await proximityReaderDiscovery.content(for: ProximityReaderDiscovery.Topic.payment(.howToTap))
        try await proximityReaderDiscovery.presentContent(content, from: myCurrentViewController)
    } catch {
        // Handle content display errors.
    }
}
```

## Topics

### Creating a discovery object

init()

Creates a new proximity reader discovery object.

### Fetching the content to display

func content(for: ProximityReaderDiscovery.Topic) async throws -> ProximityReaderDiscovery.Content

Fetches the content for the specified topic.

enum Topic

The topics you can present to someone.

struct Content

A type that represents content you can display on the current device.

var contentList: [ProximityReaderDiscovery.Content]

The content you can present for the current device.

### Displaying the information

func presentContent(ProximityReaderDiscovery.Content, from: UIViewController) async throws

Presents a sheet that teaches merchants how to use the specified feature.

### Getting relevant errors

enum ContentError

Errors that indicate a problem occurred when getting or showing content.

## Relationships

### Conforms To

- Sendable

