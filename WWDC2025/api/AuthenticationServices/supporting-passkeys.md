*   [Authentication Services](/documentation/authenticationservices)
*   [Public-Private Key Authentication](/documentation/authenticationservices/public-private-key-authentication)
*   Supporting passkeys

Article

# Supporting passkeys

Eliminate passwords for your users when they sign in to apps and websites.

## [Overview](/documentation/AuthenticationServices/supporting-passkeys#overview)

Passkeys use iCloud Keychain public key credentials, eliminating the need for passwords. Instead, they rely on biometric identification, such as Touch ID and Face ID in iOS, or a specific confirmation in macOS for generating and authenticating accounts.

As the _authenticator_, your Apple device generates a unique public-private key pair for every account it creates on a service. The authenticator retains the private key and shares its public key with the server, known as the _relying party._

Important

You need to have an associated domain with the `webcredentials` service type when making a registration or assertion request; otherwise, the request returns an error. See [Supporting associated domains](/documentation/Xcode/supporting-associated-domains) for more information.\_\_

### [Register a new account on a service](/documentation/AuthenticationServices/supporting-passkeys#Register-a-new-account-on-a-service)

To onboard users to a new service, such as an online bank or grocery delivery app, without passwords, you need to obtain a _challenge_ from the server. A challenge is data that the server generates to prove that you, as the authenticator, own the account.

The following code sets up the process of registration. Create an instance of [`ASAuthorizationPlatformPublicKeyCredentialProvider`](/documentation/authenticationservices/asauthorizationplatformpublickeycredentialprovider) and pass it your relying party identifier, which is usually the service’s domain name.

```swift
```swift
```swift
```swift
```swift
```swift
let challenge: Data // Obtain this from the server.
```
```
```swift
```swift
let userID: Data // Obtain this from the server.
```
```
```swift
```swift
let platformProvider = ASAuthorizationPlatformPublicKeyCredentialProvider(relyingPartyIdentifier: "example.com")
```
```
```swift
```swift
let platformKeyRequest = platformProvider.createCredentialRegistrationRequest(challenge: challenge, name: "Anne Johnson", userID: userID)
```
```
```swift
```swift
let authController = ASAuthorizationController(authorizationRequests: [platformKeyRequest])
```
```
authController.delegate = self
authController.presentationContextProvider = self
authController.performRequests()
```
```
```
```

Create a platform key registration request by instantiating [`ASAuthorizationPlatformPublicKeyCredentialRegistrationRequest`](/documentation/authenticationservices/asauthorizationplatformpublickeycredentialregistrationrequest). Pass the challenge, the user name, and the user ID.

Then create an instance of [`ASAuthorizationControllerDelegate`](/documentation/authenticationservices/asauthorizationcontrollerdelegate) and pass an array that contains the platform key request object. Set the authorization controller’s delegate and presentation context provider to the object that responds to the request, and then direct the controller to perform the registration request with [`performRequests()`](/documentation/authenticationservices/asauthorizationcontroller/performrequests\(\)).

Because this is a registration request, the device displays a sheet asking the user to create a new credential.

### [Connect to a service with an existing account](/documentation/AuthenticationServices/supporting-passkeys#Connect-to-a-service-with-an-existing-account)

After the user establishes an account with a relying party, they can connect to that service and authenticate using an assertion request.

To start the assertion request, obtain the challenge from the server, then create an instance of [`ASAuthorizationPlatformPublicKeyCredentialProvider`](/documentation/authenticationservices/asauthorizationplatformpublickeycredentialprovider) and set its provider to the service URL. Create the assertion request, passing in the challenge to receive an [`ASAuthorizationPlatformPublicKeyCredentialAssertionRequest`](/documentation/authenticationservices/asauthorizationplatformpublickeycredentialassertionrequest).

Create the authorization controller by encapsulating the platform key request in an array. You can pass additional assertion requests in the array, such as passwords and the Sign in with Apple service. The sheet displays whatever credentials the device has for those types.

Set the controller’s delegate and presentation context provider, and direct the authorization controller to perform the request.

```swift
```swift
```swift
```swift
```swift
```swift
let challenge: Data // Obtain this from the server.
```
```
```swift
```swift
let platformProvider = ASAuthorizationPlatformPublicKeyCredentialProvider(relyingPartyIdentifier: "example.com")
```
```
```swift
```swift
let platformKeyRequest = platformProvider.createCredentialAssertionRequest(challenge: challenge)
```
```
```swift
```swift
let authController = ASAuthorizationController(authorizationRequests: [platformKeyRequest])
```
```
authController.delegate = self
authController.presentationContextProvider = self
authController.performRequests()
```
```
```
```

If you provide an assertion request to the controller and the user has one or more credentials on the device, the device displays a sheet with the list of credentials to choose from. An error returns if there aren’t any credentials on the device. In this case, ask the user to register for the service.

### [Respond to the request](/documentation/AuthenticationServices/supporting-passkeys#Respond-to-the-request)

[`ASAuthorizationControllerDelegate`](/documentation/authenticationservices/asauthorizationcontrollerdelegate) provides information about the outcome of a registration or authentication request. Adopt this protocol to determine how to react to authorization success or errors. The following code defines [`authorizationController(controller:didCompleteWithAuthorization:)`](/documentation/authenticationservices/asauthorizationcontrollerdelegate/authorizationcontroller\(controller:didcompletewithauthorization:\)) to handle registration and assertion, as well as [`authorizationController(controller:didCompleteWithError:)`](/documentation/authenticationservices/asauthorizationcontrollerdelegate/authorizationcontroller\(controller:didcompletewitherror:\)) to handle any errors:

```swift
```swift
```swift
```swift
```swift
```swift
func authorizationController(controller: controller, didCompleteWithAuthorization: authorization) {
```
```
  if let credential = authorization.credential as? ASAuthorizationPlatformPublicKeyCredentialRegistration {
    // Take steps to handle the registration.
 } else if let credential = authorization.credential as? ASAuthorizationPlatformPublicKeyCredentialAssertion {
    // Take steps to verify the challenge.
  } else {
    // Handle other authentication cases, such as Sign in with Apple.
}
```swift
```swift
func authorizationController(controller: controller, didCompleteWithError: error) {
```
```
  // Handle the error.
}
```
```
```
```

If the authorization succeeds, obtain the credential from the authoriziation controller and determine whether it’s an [`ASAuthorizationPlatformPublicKeyCredentialRegistration`](/documentation/authenticationservices/asauthorizationplatformpublickeycredentialregistration) or an \` \`\`\`ASAuthorizationPlatformPublicKeyCredentialAssertion\`\`, then take appropriate steps to verify the credential and complete the operation with the server. If your app uses other authorization cases, such as Sign in with Apple, handle those in this delegate method, as well.

If an error occurs during the authorization, the framework calls [`authorizationController(controller:didCompleteWithError:)`](/documentation/authenticationservices/asauthorizationcontrollerdelegate/authorizationcontroller\(controller:didcompletewitherror:\)) and provides the specific error.

### [Support AutoFill](/documentation/AuthenticationServices/supporting-passkeys#Support-AutoFill)

Password AutoFill is a familiar authentication workflow for logging into apps and services. Using AutoFill, you can use passkeys alongside passwords while maintaining the same familiar user experience.

To prepare your iOS app to use AutoFill, first set your text field’s [`textContentType`](/documentation/UIKit/UITextInputTraits/textContentType) to [`username`](/documentation/UIKit/UITextContentType/username). This property lets the system know where to show the passkey suggestion. Next, call [`performAutoFillAssistedRequests()`](/documentation/authenticationservices/asauthorizationcontroller/performautofillassistedrequests\(\)). When the user taps the user name field, the system can suggest passkeys that the user saved for the app.

### [Change or reset a passkey](/documentation/AuthenticationServices/supporting-passkeys#Change-or-reset-a-passkey)

There may be times when a user needs a new passkey, for example, to recover an account or to revoke access to a passkey shared with someone else.

To change or reset a passkey, use [`createCredentialRegistrationRequest(challenge:displayName:name:userID:)`](/documentation/authenticationservices/asauthorizationsecuritykeypublickeycredentialprovider/createcredentialregistrationrequest\(challenge:displayname:name:userid:\)). The device generates a new public-private key pair. Provide the new public key to the server so that it uses the new passkey. Discard the previous public key from your server and replace it with the newly generated one.

Registering a passkey with the same user ID as an existing one overwrites the existing passkey on the user’s devices.

### [Use passkeys in a web view](/documentation/AuthenticationServices/supporting-passkeys#Use-passkeys-in-a-web-view)

To authenticate using passkeys in a [`WKWebView`](/documentation/WebKit/WKWebView) web view, configure your service’s relying party identifier as an associated domain in your app. For more information, see [Supporting associated domains](/documentation/Xcode/supporting-associated-domains).

Note

Your app can’t use passkeys to authenticate for services that you haven’t configured as the app’s associated domains.

In iOS 16.4 and later, and macOS 13.3 and later, use Javascript APIs in [`WKWebView`](/documentation/WebKit/WKWebView) to test whether passkey authentication is available. If the person has a passkey available for the relying party, `isUserVerifyingPlatformAuthenticatorAvailable()` returns `true`. If passkey AutoFill is available, `isConditionalMediationAvailable()` returns `true`.

## [See Also](/documentation/AuthenticationServices/supporting-passkeys#see-also)

### [Fundamentals](/documentation/AuthenticationServices/supporting-passkeys#Fundamentals)

[

Connecting to a service with passkeys](/documentation/authenticationservices/connecting-to-a-service-with-passkeys)

Allow users to sign in to a service without typing a password.

[

Supporting Security Key Authentication Using Physical Keys](/documentation/authenticationservices/supporting-security-key-authentication-using-physical-keys)

Allow users to authenticate using NFC, USB, and Lightning security keys in your app or service.