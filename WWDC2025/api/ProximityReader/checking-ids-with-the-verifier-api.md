*   [ProximityReader](/documentation/proximityreader)
*   Checking IDs with the Verifier API

Sample Code

# Checking IDs with the Verifier API

Read and verify mobile driver’s license information without any additional hardware.

[Download](https://docs-assets.developer.apple.com/published/b2924d5d3840/CheckingIDsWithTheVerifierAPI.zip)

iOS 17.0+Xcode 15.0+

## [Overview](/documentation/ProximityReader/checking-ids-with-the-verifier-api#Overview)

Note

This sample code project is associated with WWDC23 session 10114: [What’s new in Wallet and Apple Pay](https://developer.apple.com/wwdc23/10114/).

### [Configure the sample code project](/documentation/ProximityReader/checking-ids-with-the-verifier-api#Configure-the-sample-code-project)

The project contains two targets:

*   `VerifierAPISample-DisplayRequest`: This target is configured to perform a [`MobileDriversLicenseDisplayRequest`](/documentation/proximityreader/mobiledriverslicensedisplayrequest).
    
*   `VerifierAPISample-DataRequest`: This target is configured to perform a [`MobileDriversLicenseDataRequest`](/documentation/proximityreader/mobiledriverslicensedatarequest).
    

## [See Also](/documentation/ProximityReader/checking-ids-with-the-verifier-api#see-also)

### [Mobile document reader](/documentation/ProximityReader/checking-ids-with-the-verifier-api#Mobile-document-reader)

[

Adopting the Verifier API in your iPhone app](/documentation/proximityreader/adopting-the-verifier-api-in-your-iphone-app)

Configure and test ID Verifier support in your app for reading mobile documents.

[

Generating reader tokens for the Verifier API](/documentation/proximityreader/generating-reader-tokens-for-the-verifier-api)

Configure your server to generate reader tokens to prepare a device for mobile document reading.

```swift
```swift
```swift
class MobileDocumentReader
```
```

An object for configuring mobile document reading on the current device.
```
```swift
```swift
```swift
class MobileDocumentReaderSession
```
```

The object you use to start reading a mobile document.
```