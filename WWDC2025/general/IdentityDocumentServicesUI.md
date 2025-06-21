Framework

# IdentityDocumentServicesUI

Provide an interface so people can present mobile documents.

iOS 26.0+BetaiPadOS 26.0+BetamacOS 26.0+Beta

## [Overview](/documentation/IdentityDocumentServicesUI#overview)

The `IdentityDocumentServicesUI` framework contains user-interface objects that support the features in [IdentityDocumentServices](/documentation/IdentityDocumentServices). This includes types for implementing authorization UI for an [`IdentityDocumentProvider`](/documentation/identitydocumentservicesui/identitydocumentprovider) app. It also includes a controller to enable browsers to implement the Digital Credentials API.

## [Topics](/documentation/IdentityDocumentServicesUI#topics)

### [Building identity document provider authorization UI](/documentation/IdentityDocumentServicesUI#Building-identity-document-provider-authorization-UI)

```swift
```swift
```swift
```swift
protocol IdentityDocumentProvider
```
```

An app extension that provides an identity document.
```
```swift
```swift
```swift
protocol IdentityDocumentRequestScene
```
```

A scene that indicates support for a specific document request type.
```
```swift
```swift
```swift
struct ISO18013MobileDocumentRequestScene
```
```
```
```swift
```swift
```swift
struct ISO18013MobileDocumentRequestContext
```
```

An object that contains details about the ISO 18013 mobile document request.
```
```swift
```swift
```swift
struct IdentityDocumentRequestSceneBuilder
```
```

A result builder that combines one or more `IdentityDocumentRequestScene`s into a single scene.
```
```

### [Implementing the web presentment flow into your browser](/documentation/IdentityDocumentServicesUI#Implementing-the-web-presentment-flow-into-your-browser)

[

Implementing as an identity document provider](/documentation/IdentityDocumentServices/Implenting-as-an-identity-document-provider)

Add your app as an option for mobile document web presentment.

```swift
```swift
```swift
class IdentityDocumentWebPresentmentController
```
```

A controller that performs identity document requests originating from the web.
```
```swift
```swift
```swift
protocol IdentityDocumentWebPresentmentControllerDelegate
```
```

Defines a delegate that the system uses in conjunction with a web presentment controller.
```
```swift
```swift
```swift
protocol IdentityDocumentPresentmentControllerPresentationContextProviding
```
```

An interface the controller uses to receive a presentation context.
```
```swift
```swift
```swift
typealias IdentityDocumentPresentationAnchor
```
```

The presentation anchor the system uses to present your app UI.
```
```swift
```swift
```swift
protocol IdentityDocumentPresentmentControlling
```
```

A closed protocol that indicates this object is a controller that the system uses for identity document presentment.
```

Beta Software

This documentation contains preliminary information about an API or technology in development. This information is subject to change, and software implemented according to this documentation should be tested with final operating system software.

[Learn more about using Apple's beta software](https://developer.apple.com/support/beta-software/)