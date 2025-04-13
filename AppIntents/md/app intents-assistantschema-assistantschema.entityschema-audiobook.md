

- App Intents
- AssistantSchema
- AssistantSchema.EntitySchema
-  audiobook 

Instance Property

# audiobook

The app entity describes an audiobook.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+watchOS 9.0+

``` source
var audiobook: some AssistantSchemas.Entity { get }
```

## Overview

To integrate your app’s functionality with Siri and Apple Intelligence, you use Swift macros that generate additional properties and add protocol conformance for your app entity implementation.

For more information about the `.books` app intent domain, see Making ebook actions available to Siri and Apple Intelligence. For general information about app intent domains, see Integrating actions with Siri and Apple Intelligence.

The following example shows an app entity that conforms to the `.books.audiobook` schema:

```
@AssistantEntity(schema: .books.audiobook)
struct AudiobookEntity: AppEntity {
    struct Query: EntityStringQuery {
        func entities(for identifiers: [AudiobookEntity.ID]) async throws -> [AudiobookEntity] { [] }
        func entities(matching string: String) async throws -> [AudiobookEntity] { [] }
    }

    static var defaultQuery = Query()
    var displayRepresentation: DisplayRepresentation { "Audiobook" }

    let id = UUID()

    @Property
    var title: String?

    @Property
    var seriesTitle: String?

    @Property
    var author: String?

    @Property
    var genre: String?

    @Property
    var purchaseDate: Date?
}
```

