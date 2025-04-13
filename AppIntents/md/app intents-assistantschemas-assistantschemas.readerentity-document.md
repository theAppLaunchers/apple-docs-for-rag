

- App Intents
- AssistantSchemas
- AssistantSchemas.ReaderEntity
-  document 

Instance Property

# document

The app entity describes a document.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+watchOS 9.0+

``` source
var document: some AssistantSchemas.Entity { get }
```

## Mentioned in 

Making document reader actions available to Siri and Apple Intelligence

## Overview

To integrate your app’s functionality with Siri and Apple Intelligence, you use Swift macros that generate additional properties and add protocol conformance for your app entity implementation.

For more information about the `.reader` app intent domain, see Making document reader actions available to Siri and Apple Intelligence. For general information about app intent domains, see Integrating actions with Siri and Apple Intelligence.

The following example shows an app entity that conforms to the `.reader.document` schema:

```
@AssistantEntity(schema: .reader.document)
struct ReaderDocumentEntity: AppEntity {
    struct Query: EntityStringQuery {
        func entities(for identifiers: [ReaderDocumentEntity.ID]) async throws -> [ReaderDocumentEntity] { [] }
        func entities(matching string: String) async throws -> [ReaderDocumentEntity] { [] }
    }
    static var defaultQuery = Query()
    var displayRepresentation: DisplayRepresentation { "Document" }

    let id = UUID()

    @Property
    var title: String

    @Property
    var kind: ReaderDocumentKind

    @Property
    var width: Int?

    @Property
    var height: Int?
}
```

