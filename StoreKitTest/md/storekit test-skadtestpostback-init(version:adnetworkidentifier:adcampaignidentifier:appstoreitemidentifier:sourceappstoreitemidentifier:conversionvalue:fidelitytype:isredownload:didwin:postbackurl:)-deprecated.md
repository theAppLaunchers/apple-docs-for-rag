

- StoreKit Test
- SKAdTestPostback
-  init(version:adNetworkIdentifier:adCampaignIdentifier:appStoreItemIdentifier:sourceAppStoreItemIdentifier:conversionValue:fidelityType:isRedownload:didWin:postbackURL:) Deprecated

Initializer

# init(version:adNetworkIdentifier:adCampaignIdentifier:appStoreItemIdentifier:sourceAppStoreItemIdentifier:conversionValue:fidelityType:isRedownload:didWin:postbackURL:)

Creates a test postback for an in-app ad.

iOS 15.4+iPadOS 15.4+Mac Catalyst 15.4+

``` source
init?(
    version: SKAdTestPostbackVersion,
    adNetworkIdentifier: String,
    adCampaignIdentifier: Int,
    appStoreItemIdentifier: Int,
    sourceAppStoreItemIdentifier: Int,
    conversionValue: Int,
    fidelityType: Int,
    isRedownload: Bool,
    didWin: Bool,
    postbackURL: String
)
```

Deprecated

To test postbacks for SKAdNetwork version 4.0 or later, use init(version:adNetworkIdentifier:sourceIdentifier:appStoreItemIdentifier:sourceAppStoreItemIdentifier:sourceDomain:fidelityType:isRedownload:didWin:postbackURL:) instead.

## Parameters 

`version`  

SKAdTestPostbackVersion, the SKAdNetwork version. For more information about versions, see SKAdNetwork release notes.

`adNetworkIdentifier`  

Your ad network identifier. For the test environment, you may use any lowercased value. You must use the same value to verify the signature after you receive the postback on your server. Also, use the same ad network identifier in the `Info.plist` of the source app in the testing environment.

`adCampaignIdentifier`  

The campaign identifier associated with the ad.

`appStoreItemIdentifier`  

The App Store item identifier of the advertised app.

`sourceAppStoreItemIdentifier`  

The App Store item identifier of the app that displays the ad. This value is `0` in the testing environment.

`conversionValue`  

SKAdNetwork version 2.0 and later. An unsigned 6-bit value that the installed app provides by calling updateConversionValue(_:). Note: In the production environment, the conversion-value only appears in the postback if the installed app provides it, and if providing the parameter meets Apple’s privacy threshold.

`fidelityType`  

SKAdNetwork version 2.2 and later. A value of `0` indicates a view-through ad presentation; a value of `1` indicates a StoreKit-rendered ad.

`isRedownload`  

SKAdNetwork version 2.0 and later. A Boolean flag that in the production environment indicates that the customer redownloaded and reinstalled the app when the value is `true`.

`didWin`  

SKAdNetwork version 3.0 and later. A Boolean value that’s `true` if the ad network won the attribution, and `false` if the postback represents a qualifying ad impression that didn’t win the attribution.

`postbackURL`  

A URL on your server where you can receive test postbacks.

## Discussion

Create one to six test postbacks to use for unit testing. Call setPostbacks(_:) to add the test postbacks to the test session.

## See Also

### Creating test postbacks

init?(version: SKAdTestPostbackVersion, adNetworkIdentifier: String, sourceIdentifier: String, appStoreItemIdentifier: Int, sourceAppStoreItemIdentifier: Int, sourceDomain: String?, fidelityType: Int, isRedownload: Bool, didWin: Bool, postbackURL: String)

Creates a test postback for a web ad or an in-app ad.

class func winningPostbacks(withVersion: SKAdTestPostbackVersion, adNetworkIdentifier: String, sourceIdentifier: String, appStoreItemIdentifier: Int, sourceAppStoreItemIdentifier: Int, sourceDomain: String?, fidelityType: Int, isRedownload: Bool, postbackURL: String) -> [SKAdTestPostback]?

Creates a sequence of test postbacks for an in-app or web ad impression.

