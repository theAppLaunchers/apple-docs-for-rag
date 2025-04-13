

- CloudKit
-  CKShare 

Class

# CKShare

A specialized record type that manages a collection of shared records.

iOS 10.0+iPadOS 10.0+Mac Catalyst 13.1+macOS 10.12+tvOS 10.0+visionOS 1.0+watchOS 3.0+

``` source
class CKShare
```

## Overview

A share is a specialized record type that facilitates the sharing of one or more records with many participants. You store shareable records in a custom record zone in the user’s private database. As you create records in that zone, they become eligible for record zone sharing. If you want to share a specific hierarchy of related records, rather than the entire record zone, set each record’s parent property to define the relationship with its parent. CloudKit infers the shared hierarchy using only the parent property, and ignores any custom reference fields.

You create a share with either the ID of the record zone to share, or the root record, which defines the point in a record hierarchy where you want to start sharing. CloudKit shares all the records in the record zone, or every record in the hierarchy below the root. If you set the root record’s parent property, CloudKit ignores it. A record can take part in only a single share. This applies to every record in the shared record zone or hierarchy. If a record is participating in another share, any attempt to save the share fails, and CloudKit returns an alreadyShared error.

Use CKModifyRecordsOperation to save the share to the server. The initial set of records the share includes must exist on the server or be part of the same save operation to succeed. CloudKit then updates the share’s url property. Use UICloudSharingController to present options to the user for sharing the URL. Otherwise, distribute the URL to any participants you add to the share. You can allow anyone with the URL to take part in the share by setting publicPermission to a value more permissive than CKShare.ParticipantPermission.none.

Important

You must add the CKSharingSupported key to your app’s `Info.plist` file with a value of `true`. This allows the system to launch your app when a user taps or clicks the URL.

After CloudKit saves the share, a participant can fetch its corresponding metadata, which includes a reference to the share, information about the user’s participation, and, for shared hierarchies, the root record’s record ID. Create an instance of CKFetchShareMetadataOperation using the share’s URL and add it to the container’s queue to execute it. The operation returns an instance of CKShare.Metadata for each URL you provide. This is only applicable if you manually process share acceptance. If a user receives the share URL and taps or clicks it, CloudKit automatically processes their participation.

To determine the configuration of a fetched share, inspect the recordName property of its recordID. If the value is CKRecordNameZoneWideShare, the share is managing a shared record zone; otherwise, it’s managing a shared record hierarchy.

```
let isZoneWide = (metadata.share.recordID.recordName == CKRecordNameZoneWideShare)
```

CloudKit limits the number of participants in a share to 100, and each participant must have an active iCloud account. You don’t create participants. Instead, use UICloudSharingController to manage a share’s participants and their permissions. Alternatively, create an instance of CKUserIdentity.LookupInfo for each user. Provide the user’s email address or phone number, and use CKFetchShareParticipantsOperation to fetch the corresponding participants. CloudKit queries iCloud for corresponding accounts as part of the operation. If it doesn’t find an account, the server updates the participant’s userIdentity to reflect that by setting the hasiCloudAccount property to false. CloudKit associates the participant with their iCloud account when they accept the share if they launch the process by tapping or clicking the share URL.

Participants with write permissions can modify or delete any record that you include in the share. However, only the owner can delete a shared hierarchy’s root record. If a participant attempts to delete the share, CloudKit removes the participant. The share remains active for all other participants. If the owner deletes a share that manages a record hierarchy, CloudKit sets the root record’s share property to `nil`. CloudKit deletes the share if the owner of the shared heirarchy deletes its root record.

You can customize the title and image the system displays when initiating a share or accepting an invitation to participate. You can also provide a custom UTI to indicate the content of the shared records. Use the keys that CKShare.SystemFieldKey defines, as the following example shows:

```
let share = CKShare(rootRecord: album)

// Configure the share so the system displays the album's 
// name and cover when the user initiates sharing or accepts 
// an invitation to participate.
share[CKShare.SystemFieldKey.title] = album["name"]
if let cover = album["cover"] as? UIImage, let data = cover.pngData() {
    share[CKShare.SystemFieldKey.thumbnailImageData] = data
}
// Include a custom UTI that describes the share's content.
share[CKShare.SystemFieldKey.shareType] = "com.example.app.album"
```

## Topics

### Creating a Share

init(coder: NSCoder)

Creates a share from a serialized instance.

convenience init(rootRecord: CKRecord)

Creates a new share for the specified record.

init(rootRecord: CKRecord, shareID: CKRecord.ID)

Creates a new share for the specified record and record ID.

init(recordZoneID: CKRecordZone.ID)

Creates a new share for the specified record zone.

### Accessing the Share’s Attributes

var owner: CKShare.Participant

The participant that represents the share’s owner.

var currentUserParticipant: CKShare.Participant?

The participant that represents the current user.

var participants: [CKShare.Participant]

An array that contains the share’s participants.

var url: URL?

The URL for inviting participants to the share.

### Configuring the Share

var publicPermission: CKShare.ParticipantPermission

The permission for anyone with access to the share’s URL.

func addParticipant(CKShare.Participant)

Adds a participant to the share.

func removeParticipant(CKShare.Participant)

Removes a participant from the share.

class Participant

An object that describes a user’s participation in a share.

### Accessing Metadata

class Metadata

An object that describes a shared record’s metadata.

### Subscripting

enum SystemFieldKey

Constants that represent the system fields of a share.

## Relationships

### Inherits From

- CKRecord

### Conforms To

- CKRecordKeyValueSetting
- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSCoding
- NSCopying
- NSObjectProtocol
- NSSecureCoding
- Sendable
- Sequence

## See Also

### Collaboration

Sharing CloudKit Data with Other iCloud Users

Create and share private CloudKit data with other users by implementing the sharing UI.

Sharing Core Data objects between iCloud users

Use Core Data and CloudKit to synchronize data between devices of an iCloud user and share data between different iCloud users.

struct CKShareTransferRepresentation

A transfer representation the system uses to share an item.

class CKAllowedSharingOptions

An object that controls participant access and permission options.

class CKSystemSharingUIObserver

An object the system uses to monitor changes in sharing.

@MainActor class UICloudSharingController

A view controller that presents standard screens for adding and removing people from a CloudKit share record.

CKSharingSupported

A Boolean value that indicates your app supports CloudKit Sharing.

