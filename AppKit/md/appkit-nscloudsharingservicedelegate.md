

- AppKit
-  NSCloudSharingServiceDelegate 

Protocol

# NSCloudSharingServiceDelegate

A set of methods for responding to the life cycle events of the cloud-sharing service.

macOS

``` source
protocol NSCloudSharingServiceDelegate : NSSharingServiceDelegate
```

## Overview

CloudKit allows a user to share a hierarchy of records with other iCloud users. In macOS, you use NSItemProvider and NSSharingService to facilitate sharing. Register an instance of CKShare with an item provider, and then use a sharing service to present it to the user. You must initialize the service with the cloudSharing service name. If the share is new, the user can configure the share and invite other iCloud users to participate. Otherwise, they can use the service to manage the share’s participants and their permissions.

This protocol defines methods that the sharing service calls when it saves changes to a share, or deletes it. The service also asks its delegate to provide the preferred sharing options when creating a new share. Set the service’s delegate property to an object that implements this protocol. Use your implementation to provide any appropriate behavior, such as deleting a share you cache locally when the service deletes it from the server.

For more information about CloudKit sharing, see Shared Records.

## Topics

### Managing the Cloud-Sharing Service

func sharingService(NSSharingService, didCompleteForItems: [Any], error: (any Error)?)

Tells the delegate when the cloud-sharing service completes.

func sharingService(NSSharingService, didSave: CKShare)

Tells the delegate when the cloud-sharing service saves the CloudKit share.

func sharingService(NSSharingService, didStopSharing: CKShare)

Tells the delegate when the user stops sharing the CloudKit share.

func options(for: NSSharingService, share: NSItemProvider) -> NSSharingService.CloudKitOptions

Asks the delegate for the participant options for the cloud-sharing service.

struct CloudKitOptions

Constants that describe how a participant can configure a CloudKit share.

## Relationships

### Inherits From

- NSObjectProtocol
- NSSharingServiceDelegate

## See Also

### App Services

class NSSharingService

An object that facilitates the sharing of content with social media services, or with apps like Mail or Safari.

class NSSharingServicePicker

A list of sharing services that the user can choose from.

protocol NSPreviewRepresentableActivityItem

An interface you adopt in custom objects that you want to share using the macOS share sheet.

class NSSharingServicePickerToolbarItem

A toolbar item that displays the macOS share sheet.

protocol NSServicesMenuRequestor

A set of methods that support interaction with items users can share through a sharing service.

Services Functions

Configure the contents of your app’s Services menu.

