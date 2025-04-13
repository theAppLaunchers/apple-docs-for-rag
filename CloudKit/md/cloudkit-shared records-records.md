

- CloudKit
-  Shared Records 

API Collection

# Shared Records

Share one or more records with other iCloud users.

## Overview

CloudKit users can share records in their private databases with other iCloud users, which enables collaboration between the people using your app. The user that initiates sharing, the owner, handles all aspects of the collaboration, from inviting people to participate to restricting what actions the participants can perform.

CloudKit allows you to share both record zones and record hierarchies. If you want to share an unbounded collection of records that don’t have natural parent-child relationships, share their containing record zone. However, if you want to share only a specific set of related records, define an explicit record hierarchy and share that instead.

For more information, see Sharing CloudKit Data with Other iCloud Users.

### Share a Record Zone or Hierarchy

You store shareable records in a custom record zone in the user’s private database. As you create records in that zone, they become eligible for record zone sharing. If you then choose to share that record zone, CloudKit allows participants to access all the records it contains.

Alternatively, you can build a hierarchy by defining relationships between records as you create them. Set a record’s parent property to designate it as a child of the referenced record. If your data model is hierarchical, this is good practice even if you don’t plan to share the records. Whereas sharing a record zone is catch-all, sharing a record hierarchy allows you to specify exactly which records to include.

To begin sharing, create an instance of CKShare with either the ID of the record zone to share, or the root record, which defines the point in the record hierarchy where you want to start sharing. CloudKit shares all the records in the record zone, or every record in the hierarchy below the root. A record can take part in only a single share. This applies to every record in the shared record zone or hierarchy.

After you create the share, save it using CKModifyRecordsOperation. The shared records must already exist in iCloud or be part of the same save operation.

### Invite Participants

After saving the share, CloudKit assigns it a stable share URL. Use this URL to invite other users to participate. In iOS, UICloudSharingController provides a consistent and familiar experience for managing a share’s participants and their permissions, and for distributing the share URL. Use NSItemProvider and NSSharingService in macOS (with the cloudSharing service name) to achieve similar functionality. Only invited participants can join a private share. Anyone with the share URL can join a public share. For more information, see publicPermission.

When an invited user taps or clicks the share URL, CloudKit verifies they have an active iCloud account, which must match their participant details. After successful verification, the system launches your app. CloudKit provides share metadata to your app’s scene delegate or app delegate. The method the system calls varies by platform and app configuration. For more information, see CKShare.Metadata.

Important

To enable the system to launch your app when the user taps or clicks the share URL, add the `CKSharingSupported` key to the app’s `Info.plist` file. For more information, see CKSharingSupported.

### Manage Share Participation

After receiving the share metadata from CloudKit, use CKAcceptSharesOperation to confirm the user’s participation. CloudKit then creates a record zone in the participant’s shared database that provides a view into the owner’s private database. The record zone contains only the records in the share; no other data is accessible. A participant with write permissions can change or delete records in this new record zone. Any changes they make are visible to all participants.

Create a database subscription in the user’s shared database the first time they launch your app. Then, when they confirm participation in a share, iCloud notifies your app, on all of the user’s devices, of any changes to the shared records. For more information, see CKDatabaseSubscription.

To stop sharing, the share’s owner must delete the share or, for shared hierarchies, the root record. If a participant wants to leave the share, delete the share record from their shared database. Use UICloudSharingController or NSSharingService to allow a participant to stop participating. Or remove them from the share using the removeParticipant(_:) method, and then save the updated share to iCloud.

### Customize the Sharing Experience

You can use the framework’s share-related operations to implement behavior similar to that of UICloudSharingController and NSSharingService to build a custom sharing experience by following these steps:

1.  Use CKFetchShareParticipantsOperation to generate participants and add them to the share using addParticipant(_:). Your app presents a list of potential participants to the user. You can also allow the owner to add participants by entering a participant’s email address or phone number.

2.  Save the share to iCloud.

3.  Provide the share URL to the participants. You can send the URL in an email or a message, or your app might have secure, in-app chat between users to facilitate distribution of the URL.

4.  For each participant, fetch the share’s metadata using CKFetchShareMetadataOperation and the share URL.

5.  Use CKAcceptSharesOperation to confirm participation.

6.  After you share records, use the properties and methods on CKShare to manage the share’s participants.

For public shares, you can skip the first step. Accepting a public share’s metadata automatically adds the user as a participant.

## Topics

### Collaboration

Sharing CloudKit Data with Other iCloud Users

Create and share private CloudKit data with other users by implementing the sharing UI.

Sharing Core Data objects between iCloud users

Use Core Data and CloudKit to synchronize data between devices of an iCloud user and share data between different iCloud users.

class CKShare

A specialized record type that manages a collection of shared records.

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

### Share Requests

class CKFetchShareMetadataOperation

An operation that fetches metadata for one or more shares.

class Metadata

An object that describes a shared record’s metadata.

class CKAcceptSharesOperation

An operation that confirms a user’s participation in a share.

### Participants

class CKFetchShareParticipantsOperation

An operation that converts user identities into share participants.

class Participant

An object that describes a user’s participation in a share.

### Base Objects

class CKOperation

The abstract base class for all operations that execute in a database.

## See Also

### Records

Local Records

Manipulate records on-device and save changes to the server.

Remote Records

Use subscriptions and change tokens to efficiently manage modifications to remote records.

class CKSyncEngine

An object that manages the synchronization of local and remote record data.

