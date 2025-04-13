

- UIKit
- UIApplicationDelegate
-  application(\_:userDidAcceptCloudKitShareWith:) 

Instance Method

# application(\_:userDidAcceptCloudKitShareWith:)

Tells the delegate that the app now has access to shared information in CloudKit.

iOS 10.0+iPadOS 10.0+Mac Catalyst 13.1+tvOS 10.0+visionOS 1.0+

``` source
@MainActor
optional func application(
    _ application: UIApplication,
    userDidAcceptCloudKitShareWith cloudKitShareMetadata: CKShareMetadata
)
```

## Parameters 

`application`  

The shared app object.

`cloudKitShareMetadata`  

Information about the CloudKit data that is now available to the app. Use this object to retrieve information about the CKShare object and the associated records that are now available.

## Discussion

If your app doesn’t support scenes, use this method to respond to a CloudKit Sharing invitation. In your implementation, accept the share by scheduling a CKAcceptSharesOperation object that contains the metadata object in the `cloudKitShareMetadata` parameter. After the share has been accepted, you can begin fetching records and incorporating the resulting data into your app. For a scene-based app, accept the invitation in your window scene delegate’s windowScene(_:userDidAcceptCloudKitShareWith:) method.

The system launches the app, as needed, before calling this method.

