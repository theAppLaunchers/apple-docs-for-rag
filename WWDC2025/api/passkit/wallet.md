Collection

*   [PassKit (Apple Pay and Wallet)](/documentation/passkit)
*   Wallet

API Collection

# Wallet

Manage tickets, boarding passes, payment cards and other passes in the Wallet app.

## [Overview](/documentation/PassKit/wallet#overview)

To access your pass using PassKit add the Wallet capability to your app. You can choose to access all of the passes that are signed using your developer team identifier, or to access a subset of pass types. For information on adding capabilities to your app, see [Adding capabilities to your app](/documentation/Xcode/adding-capabilities-to-your-app). For information on signing a pass, see [Wallet Passes](/documentation/WalletPasses).

## [Topics](/documentation/PassKit/wallet#topics)

### [Pass library](/documentation/PassKit/wallet#Pass-library)

```swift
```swift
```swift
```swift
class PKPassLibrary
```
```

Provides an interface to the user’s library of passes.
```
```

### [General purpose passes](/documentation/PassKit/wallet#General-purpose-passes)

```swift
```swift
```swift
```swift
class PKSecureElementPass
```
```

A pass with a credential that the device stores in a certified payment information chip.
```
```swift
```swift
```swift
class PKAddSecureElementPassConfiguration
```
```

An object that describes the configuration of a secure element payment pass.
```
```swift
```swift
```swift
class PKAddSecureElementPassViewController
```
```

A view controller that manages the addition of secure element payment passes.
```
```swift
```swift
```swift
class PKPass
```
```

An object that represents a single pass.
```
```swift
```swift
```swift
class PKAddPassesViewController
```
```

Lets your app show a pass and prompt the user to add that pass to the pass library.
```
```swift
```swift
```swift
struct AsyncShareablePassConfiguration
```
```
```
```swift
```swift
```swift
class PKShareSecureElementPassViewController
```
```
```
```swift
```swift
```swift
protocol PKShareSecureElementPassViewControllerDelegate
```
```
```
```swift
```swift
```swift
class Preview
```
```
```
```swift
```swift
```swift
enum PKShareSecureElementPassResult
```
```
```
```

### [Identity passes](/documentation/PassKit/wallet#Identity-passes)

[

Requesting identity data from a Wallet pass](/documentation/passkit/requesting-identity-data-from-a-wallet-pass)

Initiate a request for identity information by prompting a user for permission and decrypting a response payload.

```swift
```swift
```swift
class PKIdentityPhotoIDDescriptor
```
```

An object you use to request information from a user’s photo ID or equivalent document.

Beta
```
```swift
```swift
```swift
class PKIdentityAnyOfDescriptor
```
```

An object you use to request information from multiple identity documents.

Beta
```
```swift
```swift
```swift
class PKIdentityDriversLicenseDescriptor
```
```

An object for requesting information from a user’s driver’s license or equivalent document.
```
```swift
```swift
```swift
class PKAddIdentityDocumentMetadata
```
```

The object for specifying the metadata necessary to provision identity documents.
```
```swift
```swift
```swift
class PKAddIdentityDocumentConfiguration
```
```

Configuration to define the identity document.
```
```swift
```swift
```swift
struct JPKIPassContents
```
```

A set of actions for viewing and updating PINs, passwords, and signing abilities associated with digital identities on the JPKI applet.
```
```swift
```swift
```swift
class PKAddIdentityDocumentConfiguration
```
```

Configuration to define the identity document.
```
```swift
```swift
```swift
class PKAddPassMetadataPreview
```
```

A preview object that contains information representing the pass you add to Wallet.
```
```swift
```swift
```swift
class PKIdentityDocumentMetadata
```
```

A set of configured metadata that defines the required information to add the corresponding pass to Wallet.
```
```swift
```swift
```swift
class PKIdentityNationalIDCardDescriptor
```
```

An object for requesting information from a user’s national ID card.
```
```swift
```swift
```swift
class PKJapanIndividualNumberCardMetadata
```
```

A class that contains metadata indicating the specific product instance to provision.
```

### [Payment passes](/documentation/PassKit/wallet#Payment-passes)

```swift
```swift
```swift
```swift
class PKPaymentPass
```
```

An object that represents a provisioned payment card for in-app payments.
```
```swift
```swift
```swift
class PKAddPaymentPassViewController
```
```

Displays an interface that lets users add cards to Apple Pay from within your app.
```
```

### [Stored-value passes](/documentation/PassKit/wallet#Stored-value-passes)

```swift
```swift
```swift
```swift
class PKTransitPassProperties
```
```

The properties of a transit pass.
```
```swift
```swift
```swift
class PKSuicaPassProperties
```
```

The properties of a pass used as a ticket for the Suica transportation system.
```
```swift
```swift
```swift
class PKStoredValuePassProperties
```
```

An object that represents the properties of a pass that contains a balance used for specific transactions, such as a transit pass or loyalty card.
```
```swift
```swift
```swift
class PKStoredValuePassBalance
```
```

An object that represents a balance that’s available for transactions, such as points or money.
```
```

### [Shareable passes](/documentation/PassKit/wallet#Shareable-passes)

```swift
```swift
```swift
```swift
class PKAddShareablePassConfiguration
```
```

An object that represents the data and action for a shared copy of pass.
```
```swift
```swift
```swift
class PKShareablePassMetadata
```
```

Information that you use to configure the sharing sheet for a pass.
```
```swift
```swift
```swift
enum PKAddShareablePassConfigurationPrimaryAction
```
```

The kind of add action that the system performs with a pass.
```
```

### [Identity sheet interactions and authorization](/documentation/PassKit/wallet#Identity-sheet-interactions-and-authorization)

[

Requesting identity data from a Wallet pass](/documentation/passkit/requesting-identity-data-from-a-wallet-pass)

Initiate a request for identity information by prompting a user for permission and decrypting a response payload.

[

Verifying Wallet identity requests](/documentation/passkit/verifying-wallet-identity-requests)

Decrypt and verify an in-app presentment request on your server.

```swift
```swift
```swift
class PKIdentityAuthorizationController
```
```

An object that presents a sheet that prompts the user to allow a request for identity information.
```
```swift
```swift
```swift
class PKIdentityRequest
```
```

An object that represents a request for identity information from a Wallet pass.
```
```swift
```swift
```swift
class PKIdentityDocument
```
```

An object that represents the response to a request.
```
```swift
```swift
```swift
class PKIdentityElement
```
```

An object that represents the elements an app requests from identity documents.
```
```swift
```swift
```swift
class PKIdentityButton
```
```

An object that displays a button to trigger the identity verification flow.
```
```swift
```swift
```swift
struct VerifyIdentityWithWalletButton
```
```

A view that displays a button for identity verification.
```
```swift
```swift
```swift
struct VerifyIdentityWithWalletButtonLabel
```
```

A type that represents the label you use with a verify identity button.
```
```swift
```swift
```swift
struct VerifyIdentityWithWalletButtonStyle
```
```

A type that represents the style you use with a verify identity button.
```

### [Digital car keys](/documentation/PassKit/wallet#Digital-car-keys)

```swift
```swift
```swift
```swift
class PKAddCarKeyPassConfiguration
```
```

A specialized configuration object that PassKit uses when it creates a digital car key.
```
```swift
```swift
```swift
class PKVehicleConnectionSession
```
```
```
```swift
```swift
```swift
protocol PKVehicleConnectionDelegate
```
```
```
```swift
```swift
```swift
enum PKVehicleConnectionSessionConnectionState
```
```
```
```

### [Extend Wallet to add issuer cards](/documentation/PassKit/wallet#Extend-Wallet-to-add-issuer-cards)

[

Implementing Wallet Extensions](/documentation/passkit/implementing-wallet-extensions)

Support adding an issued card to Apple Pay from directly within Apple Wallet using Wallet Extensions.

```swift
```swift
```swift
class PKIssuerProvisioningExtensionHandler
```
```

An abstract superclass for an app extension to add a payment card to Wallet.
```
```swift
```swift
```swift
protocol PKIssuerProvisioningExtensionAuthorizationProviding
```
```

A protocol for a UI app extension to authorize a user to add a payment card to Wallet.
```

### [Common objects](/documentation/PassKit/wallet#Common-objects)

Common data types that are used throughout the Wallet.

```swift
```swift
```swift
class PKObject
```
```

An opaque type that acts as the superclass for the pass object.
```
```swift
```swift
```swift
class PKAddPassButton
```
```

Provides a button that enables users to add passes to Wallet.
```
```swift
```swift
```swift
class PKLabeledValue
```
```

An object that can represent a detail about a payment card or other item.
```
```swift
```swift
```swift
struct AddPassToWalletButton
```
```
```
```swift
```swift
```swift
struct AddPassToWalletButtonFilter
```
```
```
```swift
```swift
```swift
struct AddPassToWalletButtonResponse
```
```
```
```swift
```swift
```swift
struct AddPassToWalletButtonStyle
```
```
```

### [Entitlements](/documentation/PassKit/wallet#Entitlements)

[`Pass Type IDs Entitlement`](/documentation/BundleResources/Entitlements/com.apple.developer.pass-type-identifiers)

A list of identifiers that specify pass types that your app can access in Wallet.

### [Errors](/documentation/PassKit/wallet#Errors)

```swift
```swift
```swift
```swift
struct PKPassKitError
```
```

Errors that the PassKit framework uses.
```
```swift
```swift
```swift
struct PKAddSecureElementPassError
```
```

An error object that PassKit uses when it adds Secure Element passes.
```
```swift
```swift
```swift
enum Code
```
```

Errors that the PassKit framework uses.
```
```swift
```swift
```swift
enum Code
```
```

Error codes for problems that occur when you add a secure element passes.
```
```swift
```swift
```swift
enum PKAddPaymentPassError
```
```

Error codes for adding payment passes.
```
```swift
```swift
```swift
struct PKIdentityError
```
```

A structure that represents an identity error.
```
```swift
```swift
```swift
enum Code
```
```

Error codes for identity operations.
```
```swift
```swift
```swift
struct PKShareSecureElementPassError
```
```
```
```swift
```swift
```swift
enum Code
```
```
```
```swift
```swift
```swift
enum PKVehicleConnectionErrorCode
```
```
```
```swift
```swift
```swift
enum PayWithApplePayButtonPaymentAuthorizationPhase
```
```
```
```swift
```swift
```swift
let PKPassKitErrorDomain: String
```
```

The error domain for PassKit errors.
```
```swift
```swift
```swift
let PKIdentityErrorDomain: String
```
```

The error domain for identity errors.
```
```swift
```swift
```swift
let PKAddSecureElementPassErrorDomain: String
```
```

The error domain for errors that occur when adding a secure pass.
```
```swift
```swift
```swift
let PKShareSecureElementPassErrorDomain: String
```
```
```
```

### [Deprecated](/documentation/PassKit/wallet#Deprecated)

```swift
```swift
```swift
```swift
struct PayLaterView
```
```

A view that displays the Apple Pay Later visual merchandising widget.

Deprecated
```
```swift
```swift
```swift
class PKPayLaterView
```
```

A view that displays the Apple Pay Later visual merchandising widget.

Deprecated
```
```

## [See Also](/documentation/PassKit/wallet#see-also)

### [Related Documentation](/documentation/PassKit/wallet#Related-Documentation)

[

Wallet Passes](/documentation/WalletPasses)

Create, distribute, and update passes for the Wallet app.