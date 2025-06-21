Framework

# ProximityReader

Read contactless physical and digital wallet cards using your iPhone.

iOS 15.4+iPadOS 15.4+Mac Catalyst 15.4+

## [Overview](/documentation/ProximityReader#Overview)

The ProximityReader framework supports _Tap to Pay on iPhone_, which allows a person’s iPhone to act as a point-of-sale device without additional hardware. ProximityReader also supports the reading of loyalty cards from the Wallet app. Use this framework to initiate the payment process from your app.

The use of this framework requires you to coordinate with a participating payment service provider that is Level 3 certified. Contact your payment provider and work with them to set up a workflow for handling payments. When you’re ready, contact Apple and request the entitlement you need to integrate Tap to Pay on iPhone support into your app. For information on requesting this entitlement, see [Setting up Tap to Pay on iPhone](/documentation/proximityreader/setting-up-the-entitlement-for-tap-to-pay-on-iphone).

Note

Tap to Pay on iPhone follows the PCI CPoC Standard, which uses Level 2 certified payment kernels and a user interface for reading contactless payment cards.

## [Topics](/documentation/ProximityReader#topics)

### [Payment card reader](/documentation/ProximityReader#Payment-card-reader)

[

Setting up Tap to Pay on iPhone](/documentation/proximityreader/setting-up-the-entitlement-for-tap-to-pay-on-iphone)

Request and configure the required entitlement to support Tap to Pay on iPhone.

[

Adding support for Tap to Pay on iPhone to your app](/documentation/proximityreader/adding-support-for-tap-to-pay-on-iphone-to-your-app)

Configure your app to use Tap to Pay on iPhone to read contactless payment cards.

```swift
```swift
```swift
class PaymentCardReader
```
```

An object you use to configure Tap to Pay on iPhone on the current device.
```
```swift
```swift
```swift
class PaymentCardReaderSession
```
```

The object you use to start reading a contactless payment or loyalty card.
```

### [Payment requests](/documentation/ProximityReader#Payment-requests)

```swift
```swift
```swift
```swift
struct PaymentCardTransactionRequest
```
```

A request for a contactless purchase or refund that includes the purchase amount and currency information.
```
```swift
```swift
```swift
struct PaymentCardVerificationRequest
```
```

A request to verify details for a contactless payment card.
```
```swift
```swift
```swift
struct PaymentCardReadResult
```
```

The result of a payment card read operation.
```
```

### [Store and Forward mode](/documentation/ProximityReader#Store-and-Forward-mode)

```swift
```swift
```swift
```swift
struct StoreAndForwardBatch
```
```

A structure that stores the data to send to the payment service provider to process.
```
```swift
```swift
```swift
struct StoreAndForwardBatchDeletionToken
```
```

A secure token that you use to delete a Store and Forward batch.
```
```swift
```swift
```swift
class StoreAndForwardPaymentCardReaderSession
```
```

The object you use to start reading a contactless payment or loyalty card in Store and Forward mode.
```
```swift
```swift
```swift
struct StoreAndForwardStatus
```
```

A structure that describes the Store and Forward session status.
```
```swift
```swift
```swift
struct PaymentCardReaderStore
```
```

A structure that manages the store that contains all the Store and Forward reads.
```
```

### [Loyalty card requests](/documentation/ProximityReader#Loyalty-card-requests)

[

Accepting loyalty passes from Wallet](/documentation/proximityreader/accepting-loyalty-passes-from-wallet)

Set up the necessary components so your app can begin using Tap to Pay on iPhone to read and issue loyalty passes.

```swift
```swift
```swift
class VASRequest
```
```

A request to read a contactless loyalty card and retrieve loyalty program identifiers for the person.
```
```swift
```swift
```swift
struct VASReadResult
```
```

The result of a request to read loyalty card information.
```

### [Merchant discovery](/documentation/ProximityReader#Merchant-discovery)

```swift
```swift
```swift
```swift
class ProximityReaderDiscovery
```
```

An object that presents a UI with information about how to use Tap to Pay on iPhone.
```
```

### [Mobile document reader](/documentation/ProximityReader#Mobile-document-reader)

[

Adopting the Verifier API in your iPhone app](/documentation/proximityreader/adopting-the-verifier-api-in-your-iphone-app)

Configure and test ID Verifier support in your app for reading mobile documents.

[

Generating reader tokens for the Verifier API](/documentation/proximityreader/generating-reader-tokens-for-the-verifier-api)

Configure your server to generate reader tokens to prepare a device for mobile document reading.

[

Checking IDs with the Verifier API](/documentation/proximityreader/checking-ids-with-the-verifier-api)

Read and verify mobile driver’s license information without any additional hardware.

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

### [Mobile document requests](/documentation/ProximityReader#Mobile-document-requests)

```swift
```swift
```swift
```swift
struct MobileDriversLicenseDisplayRequest
```
```

A mobile driver’s license request that retrieves elements from the holder and displays the results onscreen for visual inspection.
```
```swift
```swift
```swift
struct MobileDriversLicenseDataRequest
```
```

A mobile driver’s license request that retrieves elements from the holder and returns the validated document elements.
```
```swift
```swift
```swift
struct MobileDriversLicenseRawDataRequest
```
```

A mobile driver’s license request which retrieves elements from the holder and returns the raw response data for processing.
```
```swift
```swift
```swift
struct MobileNationalIDCardDisplayRequest
```
```

A mobile national ID card request that retrieves elements from the holder and displays the results onscreen for visual inspection.
```
```swift
```swift
```swift
struct MobileNationalIDCardDataRequest
```
```

A mobile national ID card request that retrieves elements from the holder and returns the validated document elements.
```
```swift
```swift
```swift
struct MobileNationalIDCardRawDataRequest
```
```

A mobile national ID card request which retrieves elements from the holder and returns the raw response data for processing.
```
```swift
```swift
```swift
struct MobileDocumentDisplayRequest
```
```

A mobile document request that retrieves elements from the holder and displays the results onscreen for visual inspection.

Beta
```
```swift
```swift
```swift
protocol MobileDocumentRequest
```
```

A type that represents a mobile document request.
```
```swift
```swift
```swift
protocol MobileDocumentDataRequest
```
```

A type that represents a mobile document data request.

Beta
```
```swift
```swift
```swift
protocol MobileDocumentRawDataRequest
```
```

A type that represents a mobile document raw data request.

Beta
```
```swift
```swift
```swift
struct MobilePhotoIDDataRequest
```
```

A photo ID request that retrieves elements from the holder and returns the validated document elements.

Beta
```
```swift
```swift
```swift
struct MobilePhotoIDRawDataRequest
```
```

A mobile driver’s license request which retrieves elements from the holder and returns the raw response data for processing.

Beta
```
```swift
```swift
```swift
struct MobileDocumentAnyOfDataRequest
```
```

A type that describes a data request for any mobile document from a group of requests.

Beta
```
```swift
```swift
```swift
struct MobileDocumentAnyOfRawDataRequest
```
```

A type that describes a raw data request for any mobile document from a group of requests.

Beta
```
```

### [Errors](/documentation/ProximityReader#Errors)

```swift
```swift
```swift
```swift
enum PaymentCardReaderError
```
```

An error type that indicates problems with the configuration of the reader.
```
```swift
```swift
```swift
enum MobileDocumentReaderError
```
```

An error type that indicates problems when preparing a mobile document reader session and performing document requests.
```
```