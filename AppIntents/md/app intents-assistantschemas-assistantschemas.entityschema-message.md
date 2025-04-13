

- App Intents
- AssistantSchemas
- AssistantSchemas.EntitySchema
-  message 

Instance Property

# message

The app entity describes an email message.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+watchOS 9.0+

``` source
var message: some AssistantSchemas.Entity { get }
```

## Overview

To integrate your app’s functionality with Siri and Apple Intelligence, you use Swift macros that generate additional properties and add protocol conformance for your app entity implementation.

For more information about the `.mail` app intent domain, see Making email actions available to Siri and Apple Intelligence. For general information about app intent domains, see Integrating actions with Siri and Apple Intelligence.

The following example shows an app entity that conforms to the `.mail.message` schema:

```
@AssistantEntity(schema: .mail.message)
struct MailMessageEntity: AppEntity {
    struct Query: EntityStringQuery {
        func entities(for identifiers: [MailMessageEntity.ID]) async throws -> [MailMessageEntity] { [] }
        func entities(matching string: String) async throws -> [MailMessageEntity] { [] }
    }

    static var defaultQuery = Query()
    var displayRepresentation: DisplayRepresentation { "Mail Message" }

    let id = UUID()

    @Property
    var to: [IntentPerson]

    @Property
    var cc: [IntentPerson]

    @Property
    var bcc: [IntentPerson]

    @Property
    var subject: String?

    @Property
    var body: String?

    @Property
    var attachments: [IntentFile]

    @Property
    var sender: IntentPerson

    @Property
    var dateSent: Date

    @Property
    var dateReceived: Date

    @Property
    var isRead: Bool

    @Property
    var isJunk: Bool

    @Property
    var isFlagged: Bool

    @Property
    var account: MailAccountEntity

    @Property
    var mailbox: MailboxEntity
}
```

