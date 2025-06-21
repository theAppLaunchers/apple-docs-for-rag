Collection

*   [Authentication Services](/documentation/authenticationservices)
*   Public-Private Key Authentication

API Collection

# Public-Private Key Authentication

Register and authenticate users with passkeys and security keys, without using passwords.

## [Overview](/documentation/AuthenticationServices/public-private-key-authentication#overview)

Eliminating passwords simplifies account creation and authentication for apps and websites. Additionally, it reduces risks that arise from the reuse of one password across multiple services, brute force attacks, and social engineering that bad actors use to obtain credential information. By implementing public-private authentication according to the [W3C Web Authentication](https://www.w3.org/TR/webauthn-2/) specification, your users no longer need to remember complicated passwords or rely on password managers.

Instead of using a password, your macOS, iOS, or iPadOS device, known as the _authenticator_, generates a public-private key pair at account creation time, and sends the public key to the server. The server, known as the _relying party_, holds the public key for subsequent authentication, and uses _assertion_ to challenge the authenticator to prove its identity is valid.

There are two forms of public-private key authentication: _passkeys_ and _security keys._ With passkeys, the device stores its public-private key pair in the user’s iCloud Keychain and syncs the keys across the user’s devices. Security keys store the public-private key pair on a physical medium, such as a security card or a USB key.

## [Topics](/documentation/AuthenticationServices/public-private-key-authentication#topics)

### [Fundamentals](/documentation/AuthenticationServices/public-private-key-authentication#Fundamentals)

[

Connecting to a service with passkeys](/documentation/authenticationservices/connecting-to-a-service-with-passkeys)

Allow users to sign in to a service without typing a password.

[

Supporting passkeys](/documentation/authenticationservices/supporting-passkeys)

Eliminate passwords for your users when they sign in to apps and websites.

[

Supporting Security Key Authentication Using Physical Keys](/documentation/authenticationservices/supporting-security-key-authentication-using-physical-keys)

Allow users to authenticate using NFC, USB, and Lightning security keys in your app or service.

### [Account registration](/documentation/AuthenticationServices/public-private-key-authentication#Account-registration)

```swift
```swift
```swift
```swift
protocol ASAuthorizationPublicKeyCredentialRegistration
```
```

An interface that credential registration requests adhere to.
```
```swift
```swift
```swift
class ASAuthorizationPlatformPublicKeyCredentialRegistration
```
```

A newly created platform credential that results from a credential registration request.
```
```swift
```swift
```swift
class ASAuthorizationSecurityKeyPublicKeyCredentialRegistration
```
```

A newly created security key credential that results from a credential registration request.
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
class ASAuthorizationPlatformPublicKeyCredentialRegistrationRequest
```
```

The object for registering a new platform public key credential.
```
```swift
```swift
```swift
class ASAuthorizationSecurityKeyPublicKeyCredentialRegistrationRequest
```
```

The object for registering a new security key credential.
```
```

### [Account authentication](/documentation/AuthenticationServices/public-private-key-authentication#Account-authentication)

```swift
```swift
```swift
```swift
protocol ASAuthorizationPublicKeyCredentialAssertion
```
```

An interface for establishing a public key-based assertion.
```
```swift
```swift
```swift
class ASAuthorizationPlatformPublicKeyCredentialAssertion
```
```

A class that represents the platform credential assertion type.
```
```swift
```swift
```swift
class ASAuthorizationSecurityKeyPublicKeyCredentialAssertion
```
```

A class that represents the security key credential assertion type.
```
```swift
```swift
```swift
protocol ASAuthorizationPublicKeyCredentialAssertionRequest
```
```

An interface for requesting a public key-based credential assertion.
```
```swift
```swift
```swift
class ASAuthorizationPlatformPublicKeyCredentialAssertionRequest
```
```

The concrete assertion request type for platform credentials.
```
```swift
```swift
```swift
class ASAuthorizationSecurityKeyPublicKeyCredentialAssertionRequest
```
```

A class that defines the assertion request type for security key credentials.
```
```

### [Credential providers](/documentation/AuthenticationServices/public-private-key-authentication#Credential-providers)

```swift
```swift
```swift
```swift
class ASAuthorizationPlatformPublicKeyCredentialProvider
```
```

A mechanism for providing public key credential requests to an app or service with iCloud Keychain.
```
```swift
```swift
```swift
class ASAuthorizationSecurityKeyPublicKeyCredentialProvider
```
```

A mechanism for providing public key credential requests to an app or service with a physical security key.
```
```

### [Request configuration](/documentation/AuthenticationServices/public-private-key-authentication#Request-configuration)

```swift
```swift
```swift
```swift
protocol ASPublicKeyCredential
```
```

An interface that defines the properties of the public key.
```
```swift
```swift
```swift
class ASAuthorizationPublicKeyCredentialParameters
```
```

An object that provides required parameters for the credential during registration.
```
```swift
```swift
```swift
struct ASCOSEAlgorithmIdentifier
```
```

An identifier for the algorithm that a credential’s key pair uses.
```
```swift
```swift
```swift
struct ASCOSEEllipticCurveIdentifier
```
```

A structure that contains the elliptic curve identifier.
```
```swift
```swift
```swift
struct ASAuthorizationPublicKeyCredentialAttestationKind
```
```

A structure that defines the types of attestations a developer can request.
```
```swift
```swift
```swift
struct ASAuthorizationPublicKeyCredentialResidentKeyPreference
```
```

A structure that specifies the relying party’s preference for resident key storage.
```
```swift
```swift
```swift
struct ASAuthorizationPublicKeyCredentialUserVerificationPreference
```
```

A structure that defines the relying party’s user verification preference.
```
```swift
```swift
```swift
protocol ASAuthorizationPublicKeyCredentialDescriptor
```
```

An interface that defines the credential identifier.
```
```swift
```swift
```swift
class ASAuthorizationPlatformPublicKeyCredentialDescriptor
```
```

An object that holds the credential.
```
```swift
```swift
```swift
class ASAuthorizationSecurityKeyPublicKeyCredentialDescriptor
```
```

An object that holds public key credential transport information.
```
```swift
```swift
```swift
struct Transport
```
```

A structure that defines the security key credential transport type.
```

[`static var allSupported: [ASAuthorizationSecurityKeyPublicKeyCredentialDescriptor.Transport]`](/documentation/authenticationservices/asauthorizationsecuritykeypublickeycredentialdescriptor/transport/allsupported)

An array of currently supported transport types.
```

## [See Also](/documentation/AuthenticationServices/public-private-key-authentication#see-also)

### [Passkeys](/documentation/AuthenticationServices/public-private-key-authentication#Passkeys)

[

API Reference

Passkey use in web browsers](/documentation/authenticationservices/passkey-use-in-web-browsers)

Register and authenticate website users by using passkeys.

[

Performing fast account creation with passkeys](/documentation/authenticationservices/performing-fast-account-creation-with-passkeys)

Allow people to quickly create an account with passkeys and associated domains.

[

Connecting to a service with passkeys](/documentation/authenticationservices/connecting-to-a-service-with-passkeys)

Allow users to sign in to a service without typing a password.