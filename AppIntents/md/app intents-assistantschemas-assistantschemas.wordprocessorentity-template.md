

- App Intents
- AssistantSchemas
- AssistantSchemas.WordProcessorEntity
-  template 

Instance Property

# template

The app entity describes a text document template.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+watchOS 9.0+

``` source
var template: some AssistantSchemas.Entity { get }
```

## Overview

To integrate your app’s functionality with Siri and Apple Intelligence, you use Swift macros that generate additional properties and add protocol conformance for your app entity implementation.

For more information about the `.wordProcessor` app intent domain, see Making word processor actions available to Siri and Apple Intelligence. For general information about app intent domains, see Integrating actions with Siri and Apple Intelligence.

The following example shows an app entity that conforms to the `.wordProcessor.template` schema:

```
@AssistantEntity(schema: .wordProcessor.template)
struct WordProcessorDocumentTemplateEntity: AppEntity {
    struct Query: EntityStringQuery {
        func entities(for identifiers: [WordProcessorDocumentTemplateEntity.ID]) async throws -> [WordProcessorDocumentTemplateEntity] { [] }
        func entities(matching string: String) async throws -> [WordProcessorDocumentTemplateEntity] { [] }
    }

    static var defaultQuery = Query()
    var displayRepresentation: DisplayRepresentation { "Text Document Template" }

    let id = UUID()

    @Property
    var name: String
}
```

