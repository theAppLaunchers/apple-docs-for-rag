Framework

# Video Subscriber Account

Support TV provider and Apple TV app functionality.

iOS 10.0+iPadOS 10.0+macOS 10.14+tvOS 10.0+visionOS 1.0+

## [Overview](/documentation/VideoSubscriberAccount#overview)

`VideoSubscriberAccount` provides APIs to help you create apps that require secure communication with a TV provider’s authentication service. The framework also informs the Apple TV app about whether someone has a subscription and the details of that subscription.

## [Topics](/documentation/VideoSubscriberAccount#topics)

### [Essentials](/documentation/VideoSubscriberAccount#Essentials)

[

Video Subscriber Account updates](/documentation/Updates/VideoSubscriberAccount)

Learn about important changes in Video Subscriber Account.

### [TV provider authentication](/documentation/VideoSubscriberAccount#TV-provider-authentication)

```swift
```swift
```swift
```swift
class VSAccountManager
```
```

The object that coordinates your app’s authentication requests with a TV provider’s authentication service.
```
```

### [TV app integration](/documentation/VideoSubscriberAccount#TV-app-integration)

```swift
```swift
```swift
```swift
struct VSAppleSubscription
```
```

An Apple streaming service customer and their subscriptions.
```
```swift
```swift
```swift
class VSSubscriptionRegistrationCenter
```
```

An object that stores subscription information that the system provides to the Apple TV app.
```
```swift
```swift
```swift
class VSAccountApplicationProvider
```
```

An object to display app-specific providers in your app.
```
```

### [User account management](/documentation/VideoSubscriberAccount#User-account-management)

[

Signing people in to their media accounts automatically](/documentation/videosubscriberaccount/signing-people-in-to-media-apps-automatically)

Implement single sign-on for media-streaming apps by managing a sign-in token on a person’s Apple Account.

```swift
```swift
```swift
class VSUserAccountManager
```
```

The object that coordinates your app’s user account actions.
```
```swift
```swift
```swift
struct VSUserAccount
```
```

An object that represents a user’s account.
```

### [Errors](/documentation/VideoSubscriberAccount#Errors)

```swift
```swift
```swift
```swift
let VSErrorDomain: String
```
```

The domain for all errors in the framework.
```
```swift
```swift
```swift
let VSErrorInfoKeySAMLResponse: String
```
```

The subscription provider’s SAML error response.
```
```swift
```swift
```swift
let VSErrorInfoKeySAMLResponseStatus: String
```
```

The subscription provider’s SAML error-response status code.
```
```swift
```swift
```swift
let VSErrorInfoKeyAccountProviderResponse: String
```
```

The account provider’s error-response object.
```
```swift
```swift
```swift
let VSErrorInfoKeyUnsupportedProviderIdentifier: String
```
```

The identifier of the unsupported subscription provider.
```
```swift
```swift
```swift
struct VSError
```
```

Error information in the framework error domain.
```
```swift
```swift
```swift
enum Code
```
```

Error codes in the framework error domain.
```
```

### [Deprecated](/documentation/VideoSubscriberAccount#Deprecated)

```swift
```swift
```swift
```swift
class VSSubscription
```
```

An object that describes a subscriber’s access to content.

Deprecated
```
```