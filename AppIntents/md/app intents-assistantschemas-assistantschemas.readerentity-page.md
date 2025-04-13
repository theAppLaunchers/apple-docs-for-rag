

- App Intents
- AssistantSchemas
- AssistantSchemas.ReaderEntity
-  page 

Instance Property

# page

The app entity describes a page.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+watchOS 9.0+

``` source
var page: some AssistantSchemas.Entity { get }
```

## Overview

To integrate your app’s functionality with Siri and Apple Intelligence, you use Swift macros that generate additional properties and add protocol conformance for your app entity implementation.

For more information about the `.reader` app intent domain, see Making document reader actions available to Siri and Apple Intelligence. For general information about app intent domains, see Integrating actions with Siri and Apple Intelligence.

The following example shows an app entity that conforms to the `.reader.page` schema:

```
@AssistantEntity(schema: .reader.page)
struct ReaderPageEntity: AppEntity {
    struct Query: EntityStringQuery {
        func entities(for identifiers: [ReaderPageEntity.ID]) async throws -> [ReaderPageEntity] { [] }
        func entities(matching string: String) async throws -> [ReaderPageEntity] { [] }
    }
    static var defaultQuery = Query()
    var displayRepresentation: DisplayRepresentation { "Page" }

    let id = UUID()

    @Property var label: String
}
```

