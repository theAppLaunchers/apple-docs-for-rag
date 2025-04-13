

- Technotes
-  TN3164: Debugging the synchronization of NSPersistentCloudKitContainer 

Article

# TN3164: Debugging the synchronization of NSPersistentCloudKitContainer

Identify and resolve synchronization issues when working with `NSPersistentCloudKitContainer`.

## Overview

When you use `NSPersistentCloudKitContainer` to manage a CloudKit-backed Core Data store, the store lives on the device to provide data to your app, the CloudKit database lives on the remote CloudKit server to hold the server truth, and `NSPersistentCloudKitContainer` synchronizes them by *exporting* the local changes from the store to the database, and *importing* the remote changes from the database to the store. For more information about `NSPersistentCloudKitContainer`, see Understanding the synchronization of NSPersistentCloudKitContainer.

A synchronization failure can happen because of a code-level issue in your data presentation layer, a configuration issue related to CloudKit, or a limit on the system side. To debug a synchronization issue, look into the system logs in Xcode console or a sysdiagnose, then identify the relevant errors. This technote describes how to identify and resolve common errors seen in the logs when working with `NSPersistentCloudKitContainer`.

## Understand when the synchronization happens

The system determines when to synchronize data. When you save data to your Core Data store, `NSPersistentCloudKitContainer` asks the system if it can export the changes; the export only proceeds after the system allows. Similarly, when getting notified of a change on a CloudKit private or shared database, it needs the system’s approval to execute an import.

A CloudKit public database doesn’t support database change notifications. When working with a CloudKit public database, `NSPersistentCloudKitContainer` needs to poll periodically for the database changes. To avoid draining the system resources, `NSPersistentCloudKitContainer` typically polls once every 30 minutes when working in the CloudKit development environment (to facilitate debugging), and up to once every 24 hours in the production environment. For more information, see WWDC20 session 10650: Sync a Core Data store with the CloudKit public database.

The goal of implementing such a mechanism is to balance the use of system resources and achieve the best overall user experience on the devices. There is no API for apps to configure the timing for the synchronization.

Note

When your data synchronizes but not immediately, it is most likely that the system intentionally defers the synchronization. To discover what really happens inside an export or import, see Understand the export and Understand the import.

## Present the latest data

When your app doesn’t show the changes the other peer exported to the CloudKit database, it can be that the data is synchronized but your app’s UI is not refreshed. To verify if that is your case, quit your app, relaunch it, and confirm that the data is now up-to-date.

Note

`NSPersistentCloudKitContainer` may import data while an app is launching. If relaunching your app causes synchronization, it may be that the system intentionally deferred the imports in the previous launch session. See Understand the import for more information.

`NSPersistentCloudKitContainer` synchronizes data when appropriate. To know the state of the synchronization, observe eventChangedNotification. To get notified that `NSPersistentCloudKitContainer` imported data to the store, observe NSPersistentStoreRemoteChange.

To keep your app’s UI up to date, consume the store’s persistent history when you get an `NSPersistentStoreRemoteChange` notification, merge the relevant changes to your viewContext, and then refresh your app’s UI. Alternatively, reset your `viewContext` to clear the context cache, fetch the data, and then refresh your app’s UI.

For a sample that demonstrates how to observe the notifications and process the persistent history, see Sharing Core Data objects between iCloud users.

When working with a CloudKit public database, `NSPersistentCloudKitContainer` doesn’t automatically synchronize object deletions because the database doesn’t support deletion tracking. To avoid presenting objects deleted by the other peer, consider the following strategy:

1.  Add a new attribute to your Core Data entities to store the date when an object is removed.

2.  When deleting an object, set its removal date to .now, rather than really removing the object from the store. This converts the `delete` to an `update`, which can be synchronized across devices.

3.  In your app’s UI, only present the objects whose removal date is `nil`.

4.  If necessary, remove the objects whose removal date is sometime after the last successful export. The **sometime** needs to be long enough for the objects to be synchronized, which can be several months for apps that users use on a regular basis.

For more information, see WWDC20 session 10650: Sync a Core Data store with the CloudKit public database.

## Configure iCloud on your devices

To synchronize data across devices via `NSPersistentCloudKitContainer`, all the devices must have iCloud turn on for your app, and be logged in with an Apple ID. Perform the following steps to configure your devices:

- Go to Settings \> Apple ID \> iCloud \> Apps Using iCloud, find your app, and select the checkbox.

- Log in the devices with an Apple ID. To synchronize a store associated with a CloudKit private database, log in the devices with a same Apple ID. For CloudKit sharing, log in the owner and participant devices with different Apple IDs.

When developing your app, if you see the synchronization works on some devices, but not on others, it may be that the CloudKit state cached on the device isn’t up to date. Perform the following steps to reset the cache:

1.  Remove your app from the device.

2.  Remove the Core Data store, if it still exists after step 1. On iOS and its variants, if the store is in an App Group container shared with other apps that need to stay, consider removing the store programmatically. On macOS, find the location of the store and remove it manually.

3.  Log out iCloud on the device, log back in with the same Apple ID, and then reboot the device. This clears the cached state related to the Apple ID.

## Configure CloudKit in your project

To use CloudKit in your app, follow the process described in Setting Up Core Data with CloudKit to configure a CloudKit container. The process has Xcode automatically generate the appropriate entitlements for your app, and associate the container with your app ID, which allows your app to access the container.

When the association doesn’t exist, `NSPersistentCloudKitContainer` hits a permission failure at run time, and generates logs with an error like the following example:

```
CoreData: error: CoreData+CloudKit: 
-[NSCloudKitMirroringDelegate recoverFromPartialError:forStore:inMonitor:]block_invoke(1943): 
: Found unknown error as part of a partial failure: 

```

Note

For better readability, the logs in this technote are formatted to fit the page size, and some information in the logs is omitted.

To confirm that your CloudKit container and app ID are correctly associated:

1.  Log in Apple’s Developer Portal with your developer account, select the Certificates, Identifiers & Profiles page, and find the app ID of your app.

2.  Click the app ID to navigate to the Capabilities page, confirm that iCloud is checked, then click Edit to navigate to the iCloud Container Assignment page.

3.  Find your CloudKit container, and confirm that it is selected.

4.  Refresh your provisioning profile. In Xcode, go to the Signing & Capabilities tab of your app target, un-select the `Automatically manage signing` checkbox, select it again, and then choose the team to have Xcode refresh the provisioning profile. If you use manual code signing, create the provisioning profile manually, and then download and install it to your Xcode.

If the portal shows that the association between your CloudKit container and app ID is correct, but the error still exists, it is most likely because the association isn’t synchronized to the CloudKit server. In that case, consider using a new CloudKit container to continue your development.

Note

You can hide a CloudKit container using CloudKit Console, as shown in WWDC22 session 10115: What’s new in CloudKit Console (the content starting at 1 minute), but can’t delete an existing container.

If your CloudKit container is already used in the production environment and switching to a new container leads to data loss, consider filing a feedback report with the following information to request manually associating your CloudKit container with your app ID:

- The app ID and the CloudKit container that trigger the permission failure.

- Screenshots that show the association between your CloudKit container and app ID in the developer portal.

## Mirror your Core Data model to CloudKit

`NSPersistentCloudKitContainer` requires that an app’s Core Data model is completely mirrored to CloudKit. When detecting a Core Data attribute or relationship not existing in the CloudKit schema, `NSPersistentCloudKitContainer` stops synchronization and generates logs like the following example:

```
CoreData: CloudKit: CoreData+CloudKit: 
-[NSCloudKitMirroringDelegate _scheduleAutomatedExportWithLabel:activity:completionHandler:]_block_invoke(3364): 
 - Finished automatic export - AppDeactivationExport - 
with result:  storeIdentifier: … success: 0 madeChanges: 0 
error: Error Domain=NSCocoaErrorDomain Code=134406 
"Request '5FFC9F71-5E39-4FE8-8E48-C7A828D9B354' was aborted 
because the mirroring delegate never successfully initialized due to error: 
' in record '' in production schema"; …> … 
44 "Batch Request Failed" CKError's omited ...}>" 
UserInfo={NSLocalizedFailureReason=Request '5FFC9F71-5E39-4FE8-8E48-C7A828D9B354' was aborted 
because the mirroring delegate never successfully initialized due to error: 
' in record '' in production schema"; …
44 "Batch Request Failed" CKError's omited …}>}
```

To completely mirror your Core Data model to CloudKit, see Create the CloudKit schema.

CloudKit doesn’t support all the features of a Core Data model. When designing your model, avoid using the unsupported features, such as unique constraints and ordered relationships. For more information, see Creating a Core Data Model for CloudKit. For an example on how to avoid duplicates, see Remove duplicate data.

Notes

If the debug build of your app synchronizes correctly but the App Store or TestFlight build doesn’t, it is most likely because you haven’t deployed your CloudKit schema to the production environment. For more information, see Deploying an iCloud Container’s Schema.

## Avoid hitting a CloudKit limit

CloudKit has some limits. For example:

- The number of record zones in a CloudKit container is limited to 1000.

- The number of record fields in a record type is limited to 256.

- The size of a record is limited 1MB. (Record fields of the `CKAsset` type are excluded to this limit.)

- The storage a user or an app can use is limited to its quota.

When your app hits a limit, `NSPersistentCloudKitContainer` generates logs with a `Limit Exceeded` error. Here is an example that happened because the record size was too large:

```
CoreData+CloudKit: -[NSCloudKitMirroringDelegate _performSetupRequest:]_block_invoke_2(1123): 
Called about a failure to save a share:  - 

```

To avoid the 256 fields per record type limit, review your CloudKit schema. If you find a record type that is close to or exceeds the limit, trace back to the associated Core Data entity, and split it into multiple entities. See Reading CloudKit Records for Core Data for how a Core Data model is mirrored to CloudKit.

For other limits, avoid them when designing your app’s architecture and workflow. If hitting a limit is inevitable, handle it appropriately. For example, whenever you create a new CloudKit share (CKShare) using share(_:to:completion:), the API creates a new shared record zone. Over time, your app may hit the 1000 record zone per container limit. To avoid that, consider reusing an existing share when appropriate, and removing empty shares using purgeObjectsAndRecordsInZone(with:in:completion:). In the case where your app inevitably hits the limit, provide an option the user to keep their data before removing a record zone.

## Avoid synchronizing a store with multiple persistent containers

When using `NSPersistentCloudKitContainer` to load a Core Data store that is already loaded by another `NSPersistentCloudKitContainer` instance, you might see an error like the following example:

```
CoreData+CloudKit: -[NSCloudKitMirroringDelegate resetAfterError:andKeepContainer:](585): 
 - resetting internal state after error: 
Error Domain=NSCocoaErrorDomain Code=134410 
"CloudKit setup failed because there is another instance of this persistent store actively syncing with CloudKit in this process."
UserInfo={NSURL=file:///private/var/mobile/Containers/Shared/AppGroup/FF9DEFCC-5FA0-4CE6-98FC-BAAB2821911F/shared.sqlite, 
NSLocalizedFailureReason=CloudKit setup failed 
because there is another instance of this persistent store actively syncing with CloudKit in this process.,
NSUnderlyingException=Illegal attempt to register a second handler for activity identifier
com.apple.coredata.cloudkit.activity.setup.A21D2FE4-14B6-4A3C-9381-A56B58117E8F}
```

This can happen when your app and extension both use `NSPersistentCloudKitContainer` to manage a shared Core Data store (even though they are different processes). When working with an extension, you don’t control its lifecycle. It is perfectly possible that your extension is launched when your app is running, or vice versa, and both of them try to load the shared store.

To avoid the conflict, consider having the app in charge of the synchronization. An extension that has the capability to present UI can remind users to launch the app to synchronize with CloudKit, if that is an appropriate user experience.

The app and extension can avoid presenting stale data by observing `.NSPersistentStoreRemoteChange` and consuming the persistent history, as discussed in Present the latest data.

The error can also happen when your app unintentionally has multiple `NSPersistentCloudKitContainer` instances that manage the same store. For example, when you set a variable that holds an `NSPersistentCloudKitContainer` instance to a new value, the instance won’t be released if a Core Data object tied to the container still exists. To avoid the situation, release all the objects before releasing the `NSPersistentCloudKitContainer` instance.

## Avoid rate limit throttles

`NSPersistentCloudKitContainer` exports every change on the Core Data store to CloudKit. A lot of changes in a short time frame are converted to a high export rate. If the rate hits a limit, the system on the device or the CloudKit server may decide to defer the synchronization to avoid draining the resources. To determine if your app hits rate limit throttles, see Understand system throttles and Understanding CloudKit throttles.

`NSPersistentCloudKitContainer` stops synchronization when hitting rate limit throttles, and automatically recovers when the throttles expire. The expiration time can be hours, and there is no API for your app to configure it. The strategy to handle rate limit throttles is to avoid them in the first place.

If your app hits the throttles, consider redesigning its architecture and workflow so it makes less changes in a longer time frame. For example, populating a large dataset in a short time frame to your Core Data store may trigger rate limit throttles, and you might be able to avoid that by separating the dataset in batches and populating them lazily, or by shipping the dataset as a local store, and then gradually moving the data to the CloudKit-back store if necessary. To manage multiple Core Data stores with a persistent container, see Linking Data Between Two Core Data Stores.

## Diagnose with a sysdiagnose

If your issue isn’t covered in the technote, consider figuring out what happens inside the synchronization process by tracing the exports and imports. For more information, see Understanding the synchronization of NSPersistentCloudKitContainer.

## Revision History

- **2024-02-20** First published.

## See Also

### Latest

TN3182: Adding privacy tracking keys to your privacy manifest

Declare the tracking domains you use in your app or third-party SDK in a privacy manifest.

TN3183: Adding required reason API entries to your privacy manifest

Declare the APIs that can potentially fingerprint devices in your app or third-party SDK in a privacy manifest.

TN3184: Adding data collection details to your privacy manifest

Declare the data your app or third-party SDK collects in a privacy manifest.

TN3181: Debugging an invalid privacy manifest

Identify common configurations that cause unsuccessful privacy manifest validation with the App Store.

TN3180: Reverting to App Store Server Notifications V1

Migrate from version 2 to version 1 of App Store Server Notifications using the Modify an App endpoint.

TN3179: Understanding local network privacy

Learn how local network privacy affects your software.

TN3178: Checking for and resolving build UUID problems

Ensure that every Mach-O image has a UUID, and that every distinct Mach-O image has its own unique UUID.

TN3177: Understanding alternate audio track groups in movie files

Learn how alternate groups collect audio tracks, and how to choose which audio track to use in your app.

TN3111: iOS Wi-Fi API overview

Explore the various Wi-Fi APIs available on iOS and their expected use cases.

TN3176: Troubleshooting Apple Pay payment processing issues

Diagnose errors that occur when processing Apple Pay payments, identify common causes, and explore potential solutions.

TN3175: Diagnosing issues with displaying the Apple Pay button on your website

Diagnose common errors received while displaying the Apple Pay button on your website by identifying the underlying causes, and explore potential solutions.

TN3174: Diagnosing issues with the Apple Pay payment sheet on your website

Diagnose errors received while presenting the Apple Pay payment sheet on your website by identifying the underlying causes of common errors and explore their potential solutions.

TN3173: Troubleshooting issues with your Apple Pay merchant identifier configuration

Diagnose errors due to invalid Apple Pay merchant identifier configurations by identifying the underlying causes of common errors and explore their potential solutions.

TN3168: Making your App Clip available in the App Store

Learn how to configure your App Clip to prevent it from being unavailable in the App Store.

TN3124: Debugging coordinate space issues

Learn techniques to help debug any coordinate space issue.

