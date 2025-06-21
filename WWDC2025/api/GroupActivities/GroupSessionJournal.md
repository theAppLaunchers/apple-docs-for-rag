*   [Group Activities](/documentation/groupactivities)
*   GroupSessionJournal

Class

# GroupSessionJournal

An object that manages file and data transfers between participants joined in a group session.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+tvOS 17.0+visionOS 1.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift

```swift
final class GroupSessionJournal
```

```
```
```
```
```
```
```

## [Mentioned in](/documentation/GroupActivities/GroupSessionJournal#mentions)

[

Synchronizing data during a SharePlay activity](/documentation/groupactivities/synchronizing-data-during-a-shareplay-activity)

## [Overview](/documentation/GroupActivities/GroupSessionJournal#overview)

A [`GroupSessionJournal`](/documentation/groupactivities/groupsessionjournal) object lets you transfer files and other data objects between participants of a shared activity. A journal object isn’t a replacement for a [`GroupSessionMessenger`](/documentation/groupactivities/groupsessionmessenger) object, which you use to transfer time-sensitive messages and commands between participants. Instead, use it to associate files and other data objects with the activity. For example, you might share images that people drag into your app as part of the activity. The journal makes these data objects available to all participants, regardless of when they joined the session.

After your app joins an activity and receives a session object, create a [`GroupSessionJournal`](/documentation/groupactivities/groupsessionjournal) object and store a strong reference to it. To add a file or data object to the group’s journal, call the [`add(_:)`](/documentation/groupactivities/groupsessionjournal/add\(_:\)) or [`add(_:metadata:)`](/documentation/groupactivities/groupsessionjournal/add\(_:metadata:\)) method with the data you want to share. The types you specify must adopt the [`Transferable`](/documentation/CoreTransferable/Transferable) protocol from the Core Transferable framework. The journal object uses that protocol to package a version of your data suitable for sending to other devices.

To receive data that a participant added to the journal, configure a task to listen for asynchronous updates to the [`attachments`](/documentation/groupactivities/groupsessionjournal/attachments-swift.property) property of your [`GroupSessionJournal`](/documentation/groupactivities/groupsessionjournal) object. When someone adds or removes an attachment, the journal updates the array and executes your task. Load the contents of an attachment using the [`load(_:)`](/documentation/groupactivities/groupsessionjournal/attachment/load\(_:\)) method of that type. You can also retrieve any attachment-specific metadata, such as a shared ID or display name, that you included with the attached file. The following example creates a task that waits on a custom image type. The `journal` variable contains a previously configured [`GroupSessionJournal`](/documentation/groupactivities/groupsessionjournal) object.

```swift
```swift
```swift
```swift
```swift
```swift
let attachmentListener = Task {
```
```
   for await attachments in journal.attachments {
       for attachment in attachments {
           let receivedItem = try await attachment.load(MyImageItem.self)
           // Do something with the item you receive.
       }
   }
}
```
```
```
```

## [Topics](/documentation/GroupActivities/GroupSessionJournal#topics)

### [Creating an attachment manager](/documentation/GroupActivities/GroupSessionJournal#Creating-an-attachment-manager)

[`convenience init<Activity>(session: GroupSession<Activity>)`](/documentation/groupactivities/groupsessionjournal/init\(session:\))

Creates a journal and associates it with the specified session of a group activity.

### [Uploading content to the session](/documentation/GroupActivities/GroupSessionJournal#Uploading-content-to-the-session)

```swift
```swift
```swift
```swift
func add<ItemType>(ItemType) async throws -> GroupSessionJournal.Attachment
```
```

Adds the specified item to the journal and begins transferring the item’s data to the other participants’ devices so they can access it.
```
```swift
```swift
```swift
func add<ItemType, MetadataType>(ItemType, metadata: MetadataType) async throws -> GroupSessionJournal.Attachment
```
```

Adds the specified item and metadata to the journal and begins transferring the data to the other participants’ devices so they can access it.
```
```

### [Downloading content from the session](/documentation/GroupActivities/GroupSessionJournal#Downloading-content-from-the-session)

```swift
```swift
```swift
```swift
var attachments: GroupSessionJournal.Attachments
```
```

The currently available attachments for you to download and incorporate into your app.
```
```swift
```swift
```swift
struct Attachments
```
```

An asynchronous sequence that contains one or more incoming attachment containers for you to process.
```
```swift
```swift
```swift
struct Attachment
```
```

A container for the data you download.
```
```

### [Removing content from the session](/documentation/GroupActivities/GroupSessionJournal#Removing-content-from-the-session)

```swift
```swift
```swift
```swift
func remove(attachment: GroupSessionJournal.Attachment) async throws
```
```

Removes the specified attachment from the journal on all sessions.
```
```

## [Relationships](/documentation/GroupActivities/GroupSessionJournal#relationships)

### [Conforms To](/documentation/GroupActivities/GroupSessionJournal#conforms-to)

*   [`Sendable`](/documentation/Swift/Sendable)
*   [`SendableMetatype`](/documentation/Swift/SendableMetatype)

## [See Also](/documentation/GroupActivities/GroupSessionJournal#see-also)

### [File and data transfer](/documentation/GroupActivities/GroupSessionJournal#File-and-data-transfer)

[

Synchronizing data during a SharePlay activity](/documentation/groupactivities/synchronizing-data-during-a-shareplay-activity)

Send custom messages and data between devices to synchronize content for your activity, and incorporate messages your app receives from other participants.

```swift
```swift
```swift
class GroupSessionMessenger
```
```

An object that transfers app-specific data between the devices joined in a group session.
```