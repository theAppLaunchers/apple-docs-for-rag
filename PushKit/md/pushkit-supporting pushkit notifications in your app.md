

- PushKit
-  Supporting PushKit Notifications in Your App 

Article

# Supporting PushKit Notifications in Your App

Declare the types of PushKit notifications your app supports and configure objects to respond to them.

## Overview

You must configure your app to handle PushKit-related notifications, and you must supply a server to generate those notifications. In your app, you tell PushKit what types of push notifications your app handles, and you write code to respond when a notification arrives. You use your server to generate the push notifications that your app receives. When a user initiates a call with your service, your server creates a push notification request for that call and sends it to Apple Push Notification service (APNs), which delivers that notification to the user’s device.

For information about how to set up a server to generate push notifications, see Setting up a remote notification server.

### Enable Push Notification Support for Your App

Apps must have the proper entitlements to receive push notifications. To create these entitlements, add the push notifications capability to your Xcode project. When you add this capability, Xcode adds the APS Environment Entitlement to your app and configures your App ID with the push notification service for development purposes.

Note

If you create an explicit App ID for your app, you can also add the push notification service manually by configuring the App ID from your Developer Account page.

### Register Your App with PushKit at Launch Time

The system can’t deliver push notifications to your app until you create a PKPushRegistry object and specify the types of notifications you support. Typically, you create this object at launch time and store a reference to it for the duration of your app’s runtime. The following example shows how to create this object and configure it with the Voice-over-IP (VoIP) push type. During configuration, always specify a delegate object to receive notifications.

- Swift
- Objective-C

```
func registerForVoIPPushes() {
    self.voipRegistry = PKPushRegistry(queue: nil)
    self.voipRegistry.delegate = self
    self.voipRegistry.desiredPushTypes = [.voIP]
}
```

```
- (void) registerForVoIPPushes {
   self.voipRegistry = [[PKPushRegistry alloc] initWithQueue:nil];
   self.voipRegistry.delegate = self;

   // Initiate registration.
   self.voipRegistry.desiredPushTypes = [NSSet setWithObject:PKPushTypeVoIP];
   }
```

Assigning a value to the desiredPushTypes property begins the registration process, so always update that property last. The server reports the success or failure of the registration process to your delegate object.

### Send the Device Token to Your Server

In order to deliver notifications to a user device, your server must know the address of that device. PushKit provides the address to you in the form of a device token, which is an opaque data object. When you register your app’s supported push types, the PKPushRegistry object creates a PKPushCredentials object and delivers it to your delegate’s pushRegistry(_:didUpdate:for:) method. The credentials object contains the device token for the current device.

Upon receiving a device token, forward it to your server along with any other information you need to identify the user, such as their account unique identifier. To ensure the security of the user’s information, always encrypt the token and all user data before sending it over the network. On your server, store device tokens securely with the user’s other account details. Because users can run your app on multiple devices, be prepared to handle multiple tokens for each notification type your app supports.

For information about how to set up your server to handle push notifications, see Setting up a remote notification server.

### Generate Push Notifications Using the Device Token

When you have data to send to the user, generate an appropriate POST request and send it to APNs. A VoIP service generates a request each time it receives an incoming call for the user. An app with a complication might generate a request whenever it receives urgent updates for that complication.

Each POST request contains a JSON payload with the data you want to send to the user. For most notification types, you may send up to 4 KB (4096 bytes) of data in your payload, but for VoIP notifications, the limit is 5 KB (5120 bytes). Include information in the payload that your app needs to respond. For example, include the new data you want your watchOS complication to display. If you cannot fit all of the data in the payload, your app can open a network connection and fetch any additional data it needs.

For information about how to construct and send POST requests to APNs, see Sending notification requests to APNs. For specific information on how to configure VoIP push notifications, see Responding to VoIP Notifications from PushKit.

## See Also

### Registration

class PKPushRegistry

An object that requests the delivery and handles the receipt of PushKit notifications.

protocol PKPushRegistryDelegate

The methods that you use to handle incoming PushKit notifications and registration events.

class PKPushCredentials

An object that encapsulates the device token you use to deliver push notifications to your app.

