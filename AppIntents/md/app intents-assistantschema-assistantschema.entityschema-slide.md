

- App Intents
- AssistantSchema
- AssistantSchema.EntitySchema
-  slide 

Instance Property

# slide

The app entity describes a slide.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+watchOS 9.0+

``` source
var slide: some AssistantSchemas.Entity { get }
```

## Overview

To integrate your app’s functionality with Siri and Apple Intelligence, you use Swift macros that generate additional properties and add protocol conformance for your app entity implementation.

For more information about the `.presentation` app intent domain, see Making presentation actions available to Siri and Apple Intelligence. For general information about app intent domains, see Integrating actions with Siri and Apple Intelligence.

The following example shows an app entity that conforms to the `.presentation.slide` schema:

```
@AssistantEntity(schema: .presentation.slide)
struct PresentationSlideEntity: AppEntity {
    struct Query: EntityStringQuery {
        func entities(for identifiers: [PresentationSlideEntity.ID]) async throws -> [PresentationSlideEntity] { [] }
        func entities(matching string: String) async throws -> [PresentationSlideEntity] { [] }
    }

    static var defaultQuery = Query()
    var displayRepresentation: DisplayRepresentation { "Presentation Slide" }

    let id = UUID()

    @Property
    var presentation: PresentationEntity

    @Property
    var slideIndex: Int?

    @Property
    var title: String?
}
```

