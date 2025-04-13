

- CallKit
-  Preparing your app to be the default calling app 

Article

# Preparing your app to be the default calling app

Configure your CallKit or LiveCommunicationKit app so people can set it as the default calling app on their device.

## Overview

In iOS and iPadOS 18.2 and later, a person may select an app other than the Phone app or FaceTime to handle calls. A calling app handles `tel:` URLs the system sends to it. For example, when someone selects your app as the default calling app, tapping on a telephone number in a contact card initiates an attempt to place the call using your app.

If your app places phone calls and you wish to optionally become the default calling app, there are several steps you need to take.

### Add the Default Calling App entitlement to your project

Add the `com.apple.developer.calling-app` entitlement to the `.entitlements` file in your app’s Xcode project. For instructions on how to add this entitlement, see Default Calling App.

### Apply the fallback URL scheme in your app

In cases where your app can’t handle the provided phone number, you may wish to have the call fall back to the operating system to handle it as a cellular phone call. Your app can do this by adopting the `telephony:` URL scheme as the fallback handler for the scene(_:continue:) delegate callback. For example:

```
    let handle = userActivity.startCallHandle // The `UserActivity` structure the system provides; the `startCallHandle` property is the phone number the system is passing to your app.
    var urlComponents = URLComponents()
    urlComponents.scheme = "telephony"
    urlComponents.path = handle  

    guard let url = urlComponents.url else { return } 

    UIApplication.shared.open(url)
```

Note

Only use the `telephony:` URL scheme as a fallback behavior in response to a person’s explicit action in your app, such as clicking a call button after your app presents the proposed number to call.

For more information on VoIP calling related intents, see INStartCallIntent.

### Prepare your app for submission to App Store Connect

To submit your app to App Store Connect, your app needs to meet the following criteria:

- The `com.apple.developer.calling-app` entitlement is in its `.entitlements` file, and it’s set to a value of `true`.

- The `Info.plist` file has the `UIBackgroundModes` property array and contains an entry with the string `voip`.

- Your app links to either the CallKit or LiveCommunicationKit frameworks.

Tip

To add a `voip` entry in the `Info.plist` file’s `UIBackgroundModes` property array, select the “App provides Voice over IP services” option from the dropdown menu.

## See Also

### Essentials

class CXProvider

An object that represents a telephony provider.

protocol CXProviderDelegate

A collection of methods that a telephony provider object calls.

class CXProviderConfiguration

An encapsulation of the configuration of a provider object.

Making and receiving VoIP calls

Initiate outgoing calls with VoIP and configure your app to receive incoming calls.

VoIP calling with CallKit

Use the CallKit framework to integrate native VoIP calling.

