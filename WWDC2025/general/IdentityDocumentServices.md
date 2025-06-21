Framework

# IdentityDocumentServices

Share mobile documents using the Digital Credentials API.

iOS 26.0+BetaiPadOS 26.0+BetamacOS 26.0+Beta

## [Overview](/documentation/IdentityDocumentServices#overview)

Identity Document Services enables the presentment of identity documents on device and web browser support for the Digital Credentials API. Once authorized, a person can select your app during a identity documents request, where they can authorize the presentment of identification through a UI you create with [IdentityDocumentServicesUI](/documentation/IdentityDocumentServicesUI).

This framework also enables web browsers to implement the presentment flow for the Digital Credentials API. With web browser support, a person can present identity documents locally on their device or remotely on another device using the same iCloud account. Identity documents can include documents such as a driver’s license or identity card.

## [Topics](/documentation/IdentityDocumentServices#topics)

### [Essentials](/documentation/IdentityDocumentServices#Essentials)

[

Requesting a mobile document on the web](/documentation/identitydocumentservices/requesting-a-mobile-document-on-the-web)

Send a request for mobile document information for apps installed on a device.

[

Implementing as an identity document provider](/documentation/identitydocumentservices/implenting-as-an-identity-document-provider)

Add your app as an option for mobile document web presentment.

### [Registering as an identity document provider](/documentation/IdentityDocumentServices#Registering-as-an-identity-document-provider)

[`actor IdentityDocumentProviderRegistrationStore`](/documentation/identitydocumentservices/identitydocumentproviderregistrationstore)

A store that notifies the system which documents an app has available for presentment.

```swift
```swift
```swift
protocol IdentityDocumentRegistration
```
```

A protocol that defines an identity document registration.
```
```swift
```swift
```swift
struct MobileDocumentRegistration
```
```

A type you use to register mobile documents.
```

### [Implementing the web presentment flow into your browser](/documentation/IdentityDocumentServices#Implementing-the-web-presentment-flow-into-your-browser)

```swift
```swift
```swift
```swift
struct IdentityDocumentWebPresentmentRawRequestValidator
```
```

A type that contains functions for validating the incoming web presentment raw request.
```
```swift
```swift
```swift
protocol IdentityDocumentWebPresentmentRequest
```
```

A closed protocol that indicates that the system uses this object to perform an identity document web presentment
```
```swift
```swift
```swift
struct ISO18013MobileDocumentRequest
```
```

A type that represents an incoming ISO 18013-5 mobile document request.
```
```swift
```swift
```swift
protocol IdentityDocumentWebPresentmentResponse
```
```

A closed protocol that indicates that the system uses this object to represent a web presentment response.
```
```swift
```swift
```swift
struct ISO18013MobileDocumentResponse
```
```

A type representing the document response from a web presentment request.
```
```swift
```swift
```swift
struct IdentityDocumentWebPresentmentRawRequest
```
```

A struct that defines the type that represents a raw web presentment request.
```
```

### [Errors](/documentation/IdentityDocumentServices#Errors)

```swift
```swift
```swift
```swift
enum IdentityDocumentWebPresentmentError
```
```

An error type thrown from the identity document web presentment controller.
```
```

Beta Software

This documentation contains preliminary information about an API or technology in development. This information is subject to change, and software implemented according to this documentation should be tested with final operating system software.

[Learn more about using Apple's beta software](https://developer.apple.com/support/beta-software/)