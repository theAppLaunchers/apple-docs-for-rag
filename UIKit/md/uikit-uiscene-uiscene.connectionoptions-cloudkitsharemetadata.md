

- UIKit
- UIScene
- UIScene.ConnectionOptions
-  cloudKitShareMetadata 

Instance Property

# cloudKitShareMetadata

Information about the CloudKit data that’s now available to the app.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.1+tvOS 13.0+visionOS 1.0+

``` source
@MainActor
var cloudKitShareMetadata: CKShareMetadata? { get }
```

## Discussion

If an invitation to share CloudKit data is available at scene-connection time, this property contains the metadata you use to accept that invitation. Use the information in the object to create and schedule a CKAcceptSharesOperation object. After your operation object finishes successfully, you can begin fetching records and incorporating the resulting data into your app.

