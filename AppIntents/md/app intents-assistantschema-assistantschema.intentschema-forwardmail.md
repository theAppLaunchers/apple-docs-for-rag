

- App Intents
- AssistantSchema
- AssistantSchema.IntentSchema
-  forwardMail 

Instance Property

# forwardMail

The app intent conforms to the schema for forwarding an email message.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+watchOS 9.0+

``` source
var forwardMail: some AssistantSchemas.Intent { get }
```

## Overview

To integrate your app’s functionality with Siri and Apple Intelligence, you use Swift macros that generate additional properties and add protocol conformance for your app intent implementation.

For more information about the `.mail` app intent domain, see Making email actions available to Siri and Apple Intelligence. For general information about app intent domains, see Integrating actions with Siri and Apple Intelligence.

The following example shows an app intent that conforms to the `.mail.forwardMail` schema:

```
@AssistantIntent(schema: .mail.forwardMail)
struct ForwardMailIntent: AppIntent {
    @Parameter
    var to: [IntentPerson]

    @Parameter
    var cc: [IntentPerson]

    @Parameter
    var bcc: [IntentPerson]

    @Parameter
    var subject: String?

    @Parameter
    var body: String?

    @Parameter
    var account: MailAccountEntity?

    @Parameter
    var attachments: [IntentFile]

    @Parameter
    var target: MailMessageEntity

    func perform() async throws -> some IntentResult {
        .result()
    }
}
```

