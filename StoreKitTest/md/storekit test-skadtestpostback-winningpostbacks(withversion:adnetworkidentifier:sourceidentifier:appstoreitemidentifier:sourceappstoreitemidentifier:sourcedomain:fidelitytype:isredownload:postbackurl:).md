

- StoreKit Test
- SKAdTestPostback
-  winningPostbacks(withVersion:adNetworkIdentifier:sourceIdentifier:appStoreItemIdentifier:sourceAppStoreItemIdentifier:sourceDomain:fidelityType:isRedownload:postbackURL:) 

Type Method

# winningPostbacks(withVersion:adNetworkIdentifier:sourceIdentifier:appStoreItemIdentifier:sourceAppStoreItemIdentifier:sourceDomain:fidelityType:isRedownload:postbackURL:)

Creates a sequence of test postbacks for an in-app or web ad impression.

iOS 16.4+iPadOS 16.4+Mac Catalyst 16.4+

``` source
class func winningPostbacks(
    withVersion version: SKAdTestPostbackVersion,
    adNetworkIdentifier: String,
    sourceIdentifier: String,
    appStoreItemIdentifier: Int,
    sourceAppStoreItemIdentifier: Int,
    sourceDomain: String?,
    fidelityType: Int,
    isRedownload: Bool,
    postbackURL: String
) -> [SKAdTestPostback]?
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

SKAdNetwork version 2.0 and later. In the production environment, a Boolean flag that indicates that the customer redownloaded and reinstalled the app when the value is `true`.

`postbackURL`  

A URL on your server where you can receive test postbacks.

## Return Value

An array containing a winning postback for each conversion window.

## Discussion

This method provides parameters to create test postbacks for either an in-app ad or a web ad. To create test postbacks for an in-app ad, provide an empty string for `sourceDomain`.

For more information about the conversion windows corresponding to each postback, see Receiving postbacks in multiple conversion windows.

## See Also

### Creating test postbacks

init?(version: SKAdTestPostbackVersion, adNetworkIdentifier: String, sourceIdentifier: String, appStoreItemIdentifier: Int, sourceAppStoreItemIdentifier: Int, sourceDomain: String?, fidelityType: Int, isRedownload: Bool, didWin: Bool, postbackURL: String)

Creates a test postback for a web ad or an in-app ad.

init?(version: SKAdTestPostbackVersion, adNetworkIdentifier: String, adCampaignIdentifier: Int, appStoreItemIdentifier: Int, sourceAppStoreItemIdentifier: Int, conversionValue: Int, fidelityType: Int, isRedownload: Bool, didWin: Bool, postbackURL: String)

Creates a test postback for an in-app ad.

Deprecated

