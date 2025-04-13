

- App Intents
- AssistantSchema
- AssistantSchema.EntitySchema
-  file 

Instance Property

# file

The app entity describes a file.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+watchOS 9.0+

``` source
var file: some AssistantSchemas.Entity { get }
```

## Overview

To integrate your app’s functionality with Siri and Apple Intelligence, you use Swift macros that generate additional properties and add protocol conformance for your app entity implementation.

For more information about the `.files` app intent domain, see Making file management actions available to Siri and Apple Intelligence. For general information about app intent domains, see Integrating actions with Siri and Apple Intelligence.

The following example shows an app entity that conforms to the `.files.file` schema:

```
@AssistantEntity(schema: .files.file)
struct ExampleFileEntity: FileEntity {
    var displayRepresentation: AppIntents.DisplayRepresentation { "Example File" }

    static var supportedContentTypes = [UTType.image]

    var id: FileEntityIdentifier

    @Property
    var creationDate: Date?

    @Property
    var fileModificationDate: Date?

    struct Query: EntityStringQuery {
        func entities(for identifiers: [ExampleFileEntity.ID]) async throws -> [ExampleFileEntity] { [] }
        func entities(matching string: String) async throws -> [ExampleFileEntity] { [] }
    }
}
```

