*   [Authentication Services](/documentation/authenticationservices)
*   ASCredentialProviderViewController

Class

# ASCredentialProviderViewController

A view controller that a credential manager app uses to extend AutoFill.

iOS 12.0+iPadOS 12.0+Mac Catalyst 14.0+macOS 11.0+visionOS 1.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift

```swift
@[`MainActor`](/documentation/Swift/MainActor)
class ASCredentialProviderViewController
```

```
```
```
```
```
```
```

## [Overview](/documentation/AuthenticationServices/ASCredentialProviderViewController#overview)

To integrate a password, passkey, or one-time passcode manager app with AutoFill:

1.  Add a Credential Provider Extension target to your project that subclasses [`ASCredentialProviderViewController`](/documentation/authenticationservices/ascredentialproviderviewcontroller). Add the [`AutoFill Credential Provider Entitlement`](/documentation/BundleResources/Entitlements/com.apple.developer.authentication-services.autofill-credential-provider) to both the extension and its containing app.
    
2.  Override the view controller’s [`prepareCredentialList(for:)`](/documentation/authenticationservices/ascredentialproviderviewcontroller/preparecredentiallist\(for:\)) method to prepare a view with a list of credentials that the person can choose from after opening your extension from the AutoFill suggestions list.
    
3.  Optionally add [`ASPasswordCredentialIdentity`](/documentation/authenticationservices/aspasswordcredentialidentity) and [`ASPasskeyCredentialIdentity`](/documentation/authenticationservices/aspasskeycredentialidentity) instances to the shared [`ASCredentialIdentityStore`](/documentation/authenticationservices/ascredentialidentitystore) to make identities available directly in the AutoFill suggestions list. Then override the [`provideCredentialWithoutUserInteraction(for:)`](/documentation/authenticationservices/ascredentialproviderviewcontroller/providecredentialwithoutuserinteraction\(for:\)-3mo23) method to provide the associated credentials when the person taps a suggestion.
    
4.  Optionally, override the [`prepareInterfaceForExtensionConfiguration()`](/documentation/authenticationservices/ascredentialproviderviewcontroller/prepareinterfaceforextensionconfiguration\(\)) method to specify a configuration interface that you can show when people first enable your credentials manager in Settings.
    

### [Receiving credential updates](/documentation/AuthenticationServices/ASCredentialProviderViewController#Receiving-credential-updates)

Apps and websites that allow sign-ins can signal updates to the operating system with the [`ASCredentialUpdater`](/documentation/authenticationservices/ascredentialupdater) class. The various “report” methods of [`ASCredentialUpdater`](/documentation/authenticationservices/ascredentialupdater) work like the “signal” methods of `PublicKeyCredential` when using WebAuthn on the web. For example, a website or app can notify credential manager apps that it updated a user name or email for a given account, allowing the manager to stay consistent with the website.

Your credential manager manager receives these updates in the “report” methods of `ASCredentialProviderViewController`. Use these calls to update your manager’s stored credential data or behavior. For example, a call to [`reportUnusedPasswordCredential(forDomain:userName:)`](/documentation/authenticationservices/ascredentialproviderviewcontroller/reportunusedpasswordcredential\(fordomain:username:\)) can indicate that someone using a passkey will no longer use a password to sign in to a given domain, or that they deleted their account. In this case, the manager should stop showing the user name and password for that domain.

Note

This class ignores calls from Mac apps built with Mac Catalyst.

## [Topics](/documentation/AuthenticationServices/ASCredentialProviderViewController#topics)

### [Getting the extension context](/documentation/AuthenticationServices/ASCredentialProviderViewController#Getting-the-extension-context)

```swift
```swift
```swift
```swift
var extensionContext: ASCredentialProviderExtensionContext
```
```

The context your credential provider extension uses to provide information to the system.
```
```swift
```swift
```swift
class ASCredentialProviderExtensionContext
```
```

A mechanism that credential provider extensions use to communicate with the system.
```
```

### [Configuring the credential provider extension](/documentation/AuthenticationServices/ASCredentialProviderViewController#Configuring-the-credential-provider-extension)

```swift
```swift
```swift
```swift
func prepareInterfaceForExtensionConfiguration()
```
```

Prepares the interface to enable the user to configure the extension.
```
```swift
```swift
```swift
class ASCredentialIdentityStore
```
```

A container that your extension fills to provide credentials through the QuickType bar.
```
```

### [Selecting a credential](/documentation/AuthenticationServices/ASCredentialProviderViewController#Selecting-a-credential)

```swift
```swift
```swift
```swift
func prepareCredentialList(for: [ASCredentialServiceIdentifier])
```
```

Prepares the interface to display a list of credentials from which the user can select.
```
```swift
```swift
```swift
func prepareCredentialList(for: [ASCredentialServiceIdentifier], requestParameters: ASPasskeyCredentialRequestParameters)
```
```

Prepares the interface to display a list of passkey and password credentials from which the user can select.
```
```swift
```swift
```swift
func prepareOneTimeCodeCredentialList(for: [ASCredentialServiceIdentifier])
```
```

Prepares the interface to display a list of one-time passcodes (OTPs) that people can select from.
```
```swift
```swift
```swift
func prepareInterface(forPasskeyRegistration: any ASCredentialRequest)
```
```

Prepare the view controller to show user interface for registering a new passkey.
```
```swift
```swift
```swift
func prepareInterfaceToProvideCredential(for: any ASCredentialRequest)
```
```

Prepare the view controller to show user interface for providing the requested credential.
```
```swift
```swift
```swift
func provideCredentialWithoutUserInteraction(for: any ASCredentialRequest)
```
```

Attempts to provide the user-requested credential with no further user interaction.
```
```swift
```swift
```swift
func performWithoutUserInteractionIfPossible(passkeyRegistration: ASPasskeyCredentialRequest)
```
```

Perform a conditional passkey registration, if possible.
```
```swift
```swift
```swift
class ASCredentialServiceIdentifier
```
```

An identifier representing a particular service for which the user needs a credential, like a web site.
```
```swift
```swift
```swift
protocol ASCredentialRequest
```
```

A protocol that describes a request from the user for your extension to provide a credential.
```
```swift
```swift
```swift
class ASPasswordCredentialRequest
```
```

A class that represents a request to supply a password credential.
```
```swift
```swift
```swift
class ASOneTimeCodeCredentialRequest
```
```
```
```swift
```swift
```swift
protocol ASAuthorizationPublicKeyCredentialRegistrationRequest
```
```

An interface that defines properties for a credential registration request.
```
```swift
```swift
```swift
class ASPasskeyCredentialRequest
```
```

A class that represents a request to supply a passkey credential.
```
```swift
```swift
```swift
class ASPasskeyCredentialRequestParameters
```
```

A class that represents information about a passkey credential request.
```
```

### [Providing text to AutoFill](/documentation/AuthenticationServices/ASCredentialProviderViewController#Providing-text-to-AutoFill)

```swift
```swift
```swift
```swift
func prepareInterfaceForUserChoosingTextToInsert()
```
```

Prepare the view controller to show a list of all insertable text with user selectable fields.
```
```

### [Recognizing errors](/documentation/AuthenticationServices/ASCredentialProviderViewController#Recognizing-errors)

```swift
```swift
```swift
```swift
struct ASExtensionError
```
```

A credential provider extension error.
```
```swift
```swift
```swift
let ASExtensionErrorDomain: String
```
```

The domain for a credential provider extension error.
```
```swift
```swift
```swift
enum Code
```
```

The codes for a credential provider extension error.
```
```

### [Accessing settings](/documentation/AuthenticationServices/ASCredentialProviderViewController#Accessing-settings)

```swift
```swift
```swift
```swift
class ASSettingsHelper
```
```

A class that opens Settings and navigates to the settings for configuring credential providers.
```
```

### [Receiving credential updates](/documentation/AuthenticationServices/ASCredentialProviderViewController#Receiving-credential-updates)

```swift
```swift
```swift
```swift
func reportAllAcceptedPublicKeyCredentials(forRelyingParty: String, userHandle: Data, acceptedCredentialIDs: [Data])
```
```

Receives a report from the system that a relying party sent a snapshot of all accepted credentials for an account.
```
```swift
```swift
```swift
func reportPublicKeyCredentialUpdate(forRelyingParty: String, userHandle: Data, newName: String)
```
```

Receives a report from the system that a relying party indicated that a passkey’s user name updated.
```
```swift
```swift
```swift
func reportUnknownPublicKeyCredential(forRelyingParty: String, credentialID: Data)
```
```

Receives a report from the system that a relying party indicated a passkey credential is invalid.
```
```swift
```swift
```swift
func reportUnusedPasswordCredential(forDomain: String, userName: String)
```
```

Receives a report from the system that a relying party indicatd that a password credential isn’t needed anymore for a given user name.
```
```

### [Deprecated methods](/documentation/AuthenticationServices/ASCredentialProviderViewController#Deprecated-methods)

```swift
```swift
```swift
```swift
func provideCredentialWithoutUserInteraction(for: ASPasswordCredentialIdentity)
```
```

Attempts to provide the user-requested credential with no further user interaction.

Deprecated
```
```swift
```swift
```swift
func prepareInterfaceToProvideCredential(for: ASPasswordCredentialIdentity)
```
```

Prepares the interface for a user interaction, like a database login, that enables it to access and return the credential for the given identity.

Deprecated
```
```

## [Relationships](/documentation/AuthenticationServices/ASCredentialProviderViewController#relationships)

### [Inherits From](/documentation/AuthenticationServices/ASCredentialProviderViewController#inherits-from)

*   [`NSViewController`](/documentation/AppKit/NSViewController)
*   [`UIViewController`](/documentation/UIKit/UIViewController)

### [Conforms To](/documentation/AuthenticationServices/ASCredentialProviderViewController#conforms-to)

*   [`CVarArg`](/documentation/Swift/CVarArg)
*   [`CustomDebugStringConvertible`](/documentation/Swift/CustomDebugStringConvertible)
*   [`CustomStringConvertible`](/documentation/Swift/CustomStringConvertible)
*   [`Equatable`](/documentation/Swift/Equatable)
*   [`Hashable`](/documentation/Swift/Hashable)
*   [`NSCoding`](/documentation/Foundation/NSCoding)
*   [`NSEditor`](/documentation/AppKit/NSEditor)
*   [`NSExtensionRequestHandling`](/documentation/Foundation/NSExtensionRequestHandling)
*   [`NSObjectProtocol`](/documentation/ObjectiveC/NSObjectProtocol)
*   [`NSSeguePerforming`](/documentation/AppKit/NSSeguePerforming)
*   [`NSStandardKeyBindingResponding`](/documentation/AppKit/NSStandardKeyBindingResponding)
*   [`NSTouchBarProvider`](/documentation/AppKit/NSTouchBarProvider)
*   [`NSUserActivityRestoring`](/documentation/AppKit/NSUserActivityRestoring)
*   [`NSUserInterfaceItemIdentification`](/documentation/AppKit/NSUserInterfaceItemIdentification)
*   [`Sendable`](/documentation/Swift/Sendable)
*   [`SendableMetatype`](/documentation/Swift/SendableMetatype)
*   [`UIActivityItemsConfigurationProviding`](/documentation/UIKit/UIActivityItemsConfigurationProviding)
*   [`UIAppearanceContainer`](/documentation/UIKit/UIAppearanceContainer)
*   [`UIContentContainer`](/documentation/UIKit/UIContentContainer)
*   [`UIFocusEnvironment`](/documentation/UIKit/UIFocusEnvironment)
*   [`UIPasteConfigurationSupporting`](/documentation/UIKit/UIPasteConfigurationSupporting)
*   [`UIResponderStandardEditActions`](/documentation/UIKit/UIResponderStandardEditActions)
*   [`UIStateRestoring`](/documentation/UIKit/UIStateRestoring)
*   [`UITraitChangeObservable`](/documentation/UIKit/UITraitChangeObservable-67e94)
*   [`UITraitEnvironment`](/documentation/UIKit/UITraitEnvironment)
*   [`UIUserActivityRestoring`](/documentation/UIKit/UIUserActivityRestoring)

## [See Also](/documentation/AuthenticationServices/ASCredentialProviderViewController#see-also)

### [AutoFill credentials](/documentation/AuthenticationServices/ASCredentialProviderViewController#AutoFill-credentials)

[

Providing one-time passcodes to AutoFill](/documentation/authenticationservices/providing-one-time-passcodes-to-autofill)

Help people efficiently perform multifactor authentication.

[`AutoFill Credential Provider Entitlement`](/documentation/BundleResources/Entitlements/com.apple.developer.authentication-services.autofill-credential-provider)

A Boolean value that indicates whether the app may, with user permission, provide user names and passwords for AutoFill in Safari and other apps.