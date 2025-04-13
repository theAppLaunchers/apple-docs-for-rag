

- App Intents
- AssistantSchemas
- AssistantSchemas.MailIntent
-  archiveMail 

Instance Property

# archiveMail

The app intent conforms to the schema for archiving an email message.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+watchOS 9.0+

``` source
var archiveMail: some AssistantSchemas.Intent { get }
```

## Overview

To integrate your app’s functionality with Siri and Apple Intelligence, you use Swift macros that generate additional properties and add protocol conformance for your app intent implementation.

For more information about the `.mail` app intent domain, see Making email actions available to Siri and Apple Intelligence. For general information about app intent domains, see Integrating actions with Siri and Apple Intelligence.

The following example shows an app intent that conforms to the `.mail.archiveMail` schema:

```
@AssistantIntent(schema: .mail.archiveMail)
struct ArchiveMailIntent: AppIntent {
    @Parameter
    var entities: [MailMessageEntity]

    func perform() async throws -> some IntentResult {
        .result()
    }
}
```

