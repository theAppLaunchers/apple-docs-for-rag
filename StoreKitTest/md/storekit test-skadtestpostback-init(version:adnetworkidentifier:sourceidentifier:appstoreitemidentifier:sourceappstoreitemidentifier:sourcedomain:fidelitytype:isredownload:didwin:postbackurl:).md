

- StoreKit Test
- SKAdTestPostback
-  init(version:adNetworkIdentifier:sourceIdentifier:appStoreItemIdentifier:sourceAppStoreItemIdentifier:sourceDomain:fidelityType:isRedownload:didWin:postbackURL:) 

Initializer

# init(version:adNetworkIdentifier:sourceIdentifier:appStoreItemIdentifier:sourceAppStoreItemIdentifier:sourceDomain:fidelityType:isRedownload:didWin:postbackURL:)

Creates a test postback for a web ad or an in-app ad.

iOS 16.4+iPadOS 16.4+Mac Catalyst 16.4+

``` source
init?(
    version: SKAdTestPostbackVersion,
    adNetworkIdentifier: String,
    sourceIdentifier: String,
    appStoreItemIdentifier: Int,
    sourceAppStoreItemIdentifier: Int,
    sourceDomain: String?,
    fidelityType: Int,
    isRedownload: Bool,
    didWin: Bool,
    postbackURL: String
)
```

## Parameters 

`version`  

SKAdTestPostbackVersion, the SKAdNetwork version. For more information about versions, see SKAdNetwork release notes.

`adNetworkIdentifier`  

Your ad network identifier. For the test environment, you may use any lowercased value. You must use the same value to verify the signature after you receive the postback on your server. Also, use the same ad network identifier in the `Info.plist` of the source app in the testing environment.

`sourceIdentifier`  

Four digits that represent the ad campaign.

`appStoreItemIdentifier`  

The App Store item identifier of the advertised app.

`sourceAppStoreItemIdentifier`  

The App Store item identifier of the app that displays the ad. This value is `0` in the testing environment.

`sourceDomain`  

The domain of the website that displays the ad.

`fidelityType`  

A value of `0` indicates a view-through ad presentation; a value of `1` indicates a StoreKit-rendered ad or a web ad.

`isRedownload`  

In the production environment, a Boolean flag that indicates that the customer redownloaded and reinstalled the app when the value is `true`.

`didWin`  

A Boolean value that’s `true` if the ad network won the attribution, and `false` if the postback represents a qualifying ad impression that didn’t win the attribution.

`postbackURL`  

A URL on your server where you can receive test postbacks.

## See Also

### Creating test postbacks

class func winningPostbacks(withVersion: SKAdTestPostbackVersion, adNetworkIdentifier: String, sourceIdentifier: String, appStoreItemIdentifier: Int, sourceAppStoreItemIdentifier: Int, sourceDomain: String?, fidelityType: Int, isRedownload: Bool, postbackURL: String) -> [SKAdTestPostback]?

Creates a sequence of test postbacks for an in-app or web ad impression.

init?(version: SKAdTestPostbackVersion, adNetworkIdentifier: String, adCampaignIdentifier: Int, appStoreItemIdentifier: Int, sourceAppStoreItemIdentifier: Int, conversionValue: Int, fidelityType: Int, isRedownload: Bool, didWin: Bool, postbackURL: String)

Creates a test postback for an in-app ad.

Deprecated

