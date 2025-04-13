

- App Intents
- AssistantSchemas
- AssistantSchemas.IntentSchema
-  updateEntry 

Instance Property

# updateEntry

The app intent conforms to the schema for updating a journal entry.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+watchOS 9.0+

``` source
var updateEntry: some AssistantSchemas.Intent { get }
```

## Overview

To integrate your app’s functionality with Siri and Apple Intelligence, you use Swift macros that generate additional properties and add protocol conformance for your app intent implementation.

For more information about the `.journal` app intent domain, see Making journaling actions available to Siri and Apple Intelligence. For general information about app intent domains, see Integrating actions with Siri and Apple Intelligence.

The following example shows an app intent that conforms to the `.journal.updateEntry` schema:

```
@AssistantIntent(schema: .journal.updateEntry)
struct UpdateJournalEntryIntent: AppIntent {
    @Parameter
    var target: JournalEntity

    @Parameter
    var title: String?

    @Parameter
    var message: AttributedString?

    @Parameter
    var mediaItems: [IntentFile]?

    @Parameter
    var entryDate: Date?

    @Parameter
    var location: CLPlacemark?

    func perform() async throws -> some IntentResult {
        .result()
    }
}
```

