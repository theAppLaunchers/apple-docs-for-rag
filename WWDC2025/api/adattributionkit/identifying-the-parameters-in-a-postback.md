*   [AdAttributionKit](/documentation/adattributionkit)
*   Identifying the parameters in a postback

Article

# Identifying the parameters in a postback

Interpret postback properties to understand the attribution report.

## [Overview](/documentation/AdAttributionKit/identifying-the-parameters-in-a-postback#Overview)

The lists in this article describe all the possible parameters you can get in a postback. To verify that Apple signed the postback, see [Verifying a postback](/documentation/adattributionkit/verifying-a-postback).

## [Understand the JSON stanza the framework sends](/documentation/AdAttributionKit/identifying-the-parameters-in-a-postback#Understand-the-JSON-stanza-the-framework-sends)

The JSON stanza your servers receive resembles the following:

```

```
{
  "jws-string": "eyJraWQiOiJhcHBsZS1kZXZlbG9wbWVudC1pZGVudGlmaWVyXC8xIiwiYWxnIjoiRVMyNTYifQ.eyJwb3N0YmFjay1pZGVudGlmaWVyIjoiODU1NDZFQjctRkQzOS00NEJDLTg5OTAtQzk4QTRBQzM2QTQ5IiwicHVibGlzaGVyLWl0ZW0taWRlbnRpZmllciI6MCwibWFya2V0cGxhY2UtaWRlbnRpZmllciI6ImNvbS5hcHBsZS5BcHBTdG9yZSIsImltcHJlc3Npb24tdHlwZSI6ImFwcC1pbXByZXNzaW9uIiwiYWQtbmV0d29yay1pZGVudGlmaWVyIjoiZGV2ZWxvcG1lbnQuYWRhdHRyaWJ1dGlvbmtpdCIsImRpZC13aW4iOnRydWUsInBvc3RiYWNrLXNlcXVlbmNlLWluZGV4IjowLCJjb252ZXJzaW9uLXR5cGUiOiJyZS1lbmdhZ2VtZW50Iiwic291cmNlLWlkZW50aWZpZXIiOiIxMjM0IiwiYWR2ZXJ0aXNlZC1pdGVtLWlkZW50aWZpZXIiOjEwNzM4MDI3NzU2fQ.bAdNwKd6OfHK9tofvjjua4X_JPcFTxXPQSspD9gZkinw97pY7R1aI-LSjl-oxZZF3_K2H5JK5TSEBee4_1U4oQ",
  "conversion-value": 24,
  "ad-interaction-type": "click",
  "country-code": "US"
}
```

```

The keys in this stanza may include:

`conversion-value`

(optional) An unsigned 6-bit value that the advertised app sets by calling a method to update the conversion value, such as [`updateConversionValue(_:lockPostback:)`](/documentation/adattributionkit/postback/updateconversionvalue\(_:lockpostback:\)).

`coarse-conversion-value`

(optional) Possible values are the strings `low`, `medium`, and `high`. The advertised app sets this value by calling a method to update conversion values, such as [`updateConversionValue(_:coarseConversionValue:lockPostback:)`](/documentation/adattributionkit/postback/updateconversionvalue\(_:coarseconversionvalue:lockpostback:\)).

`ad-interaction-type`

The string _view_, indicating that the postback is the result of a view-through impression, or the string _click_, indicating that it’s the result of a click-through impression.

`jws-string`

A compact JSON web signature (JWS) of the Apple-signed postback contents.

`country-code`

An ISO 3166-2 two-letter country identifier. For apps installed from the App Store, it comes from the location of the signed-in account at the time of the app install. For third-party marketplaces, it comes from the proof of download (POD) token the marketplace provides and represents the country the app is installed from. For more information on POD tokens, see [Supplying an install verification token](/documentation/appdistribution/supplying-an-install-verification-token).

## [Examine the JWS header for the encryption algorithm and key identifier](/documentation/AdAttributionKit/identifying-the-parameters-in-a-postback#Examine-the-JWS-header-for-the-encryption-algorithm-and-key-identifier)

The JWS header of the postback consists of two parameters and resembles the following structure:

```

```
{
  "kid": "apple-development-identifier/1",
  "alg": "ES256"
}
```

```

The keys for this structure are:

`alg`

The encryption algorithm Apple uses to sign the postback.

`kid`

The identifier of the key Apple uses to sign the postback.

## [Examine the JWS payload of the postback](/documentation/AdAttributionKit/identifying-the-parameters-in-a-postback#Examine-the-JWS-payload-of-the-postback)

The JWS decoded payload of the postback resembles the following structure:

```

```
{
  "postback-identifier": "85546EB7-FD39-44BC-8990-C98A4AC36A49",
  "publisher-item-identifier": 0,
  "marketplace-identifier": "com.apple.AppStore",
  "impression-type": "app-impression",
  "ad-network-identifier": "development.adattributionkit",
  "did-win": true,
  "postback-sequence-index": 0,
  "conversion-type": "re-engagement",
  "source-identifier": "1234",
  "advertised-item-identifier": 10738027756
}
```

```

The keys the framework delivers in this structure may include the following:

`advertised-item-identifier`

The app item ID of the advertised app.

`conversion-type`

The string `download` that the system returns to indicate someone purchased and downloaded the app for the first time, or the string `redownload` to indicate someone downloaded an already-purchased app. The string `re-engagement` indicates that someone reengaged with an app that they previously installed.

`marketplace-identifier`

(optional) The bundle ID of the alternative marketplace the advertised app is installed from.

`ad-network-identifier`

The string that identifies the ad network.

`impression-type`

The string `app-impression`.

`postback-sequence-index`

The possible integer values of `0`, `1`, and `2` signify the order of postbacks that result from the three conversion windows. For more information, see [Receiving postbacks in multiple conversion windows](/documentation/adattributionkit/receiving-postbacks-in-multiple-conversion-windows).

`source-identifier`

The hierarchical source identifier with two, three, or four digits.

`did-win`

A Boolean value that’s `true` if the ad network wins the attribution, or `false` if the postback represents a qualifying ad impression that doesn’t win the attribution.

`postback-identifier`

The postback’s unique identifier.

`publisher-item-identifier`

(optional) The app ID of the app that displays the ad.

## [Examine the postback’s JWS signature](/documentation/AdAttributionKit/identifying-the-parameters-in-a-postback#Examine-the-postbacks-JWS-signature)

The signature is a combination of the JSON Web Signature (JWS) header and payload components that Apple signs using its private key.

For more information about verifying the postback’s signature, see [Verifying a postback](/documentation/adattributionkit/verifying-a-postback). For more information about receiving postbacks, see [Receiving postbacks in multiple conversion windows](/documentation/adattributionkit/receiving-postbacks-in-multiple-conversion-windows).

## [Understand the crowd anonymity controlled properties](/documentation/AdAttributionKit/identifying-the-parameters-in-a-postback#Understand-the-crowd-anonymity-controlled-properties)

To help ensure crowd anonymity, Apple assigns a postback data tier to app downloads. The postback data tier determines whether certain parameters appear in the postback, as well as the number of digits in the hierarchical source identifier. The following postback parameters are subject to the postback data tier:

*   `coarse-conversion-value`
    
*   `conversion-value`
    
*   `source-identifier` (affects the number of digits the postback returns)
    
*   `publisher-item-identifier`
    
*   `marketplace-identifier`
    
*   `country-code`
    

## [See Also](/documentation/AdAttributionKit/identifying-the-parameters-in-a-postback#see-also)

### [Postback verification and parameter identification](/documentation/AdAttributionKit/identifying-the-parameters-in-a-postback#Postback-verification-and-parameter-identification)

[

Verifying a postback](/documentation/adattributionkit/verifying-a-postback)

Ensure the validity of a postback you receive after an ad conversion by verifying its cryptographic signature.