

- File Provider
- Nonreplicated File Provider extension
- Content and Change Tracking
- Tracking Your File Provider’s Changes
-  Using push notifications to signal changes 

Article

# Using push notifications to signal changes

Send push notifications to a device to signal changes from your server.

## Overview

You can signal changes by sending push notifications from a remote server, using the PushKit framework and the fileProvider push type. When the system receives the notification, it automatically calls the signalEnumerator(for:completionHandler:) method with the specified identifier. It also delivers the notification to any PKPushRegistryDelegate objects.

To use push notifications, you start by generating the signing key for your app. Next, you configure your app to receive push notifications. Finally, you send the notifications from your server. The following sections describe each step.

Important

Avoid sending unnecessary push notifications. If you send too many, Apple Push Notification service (APNs) throttles your requests.

For open files and directories, try to send push notifications only when your File Provider extension has an active enumerator for that item. This means your extension must update your server whenever an enumerator is created or invalidated. Additionally, this coordination must gracefully degrade when an internet connection is unavailable or fails.

For items in the working set, the server should always send push notifications.

### Generate the signing key

To signal changes from a remote server, you use provider authentication tokens (not provider certificates). To create an APNs key for your app, see Communicate with APNs using authentication tokens. Use the APNs key to sign your JSON Web Tokens (JWT) when sending notifications from your server.

### Enable and register for push notifications

To receive notifications, you first enable push notifications in your app. You can register to receive push notifications in either your app delegate or in your file provider extension. Finally, you send the device token to your server.

First, enable push notifications in your iOS app (not your File Provider extension). For details, see Communicate with APNs using authentication tokens.

1.  Open the Capabilities pane for your app target.

2.  Turn on push notifications.

Then, register for push notifications. You can register in your app delegate, your File Provider extension, or both.

Note

If you only register for push notifications in your app delegate and the device token changes, your app won’t receive notifications until someone launches the app. Registering in the File Provider extension means your app can update the device token the next time anyone interacts with the File Provider extension’s content.

In your `AppDelegate` or `FileProviderExtension` classes, adopt the PKPushRegistryDelegate protocol.

```
import PushKit

@UIApplicationMain
class AppDelegate: UIResponder, UIApplicationDelegate, PKPushRegistryDelegate {
    // ...
}
```

```
import PushKit

class FileProviderExtension: NSFileProviderExtension, PKPushRegistryDelegate {
    // ...
}
```

Also, create a `pushRegistry` instance variable in each class.

```
var pushRegistry: PKPushRegistry!
```

In your AppDelegate class’s application(_:didFinishLaunchingWithOptions:) method, register for push notifications.

```
func application(
    _ application: UIApplication, 
    didFinishLaunchingWithOptions launchOptions: [UIApplicationLaunchOptionsKey: Any]?
) -> Bool {
    pushRegistry = PKPushRegistry(queue: nil)
    pushRegistry.delegate = self
    pushRegistry.desiredPushTypes = [.fileProvider]
    return true
}
```

Similarly, in your FileProvider class’s `init()` method, register for push notifications.

```
override init() {
    super.init()
    pushRegistry = PKPushRegistry(queue: nil)
    pushRegistry.delegate = self
    pushRegistry.desiredPushTypes = [.fileProvider]
}
```

Finally, implement the pushRegistry(_:didUpdate:for:) delegate method in both your `AppDelegate` and `FileProvider` classes. The pushRegistry(_:didInvalidatePushTokenFor:) method is optional.

Note

The pushRegistry(_:didReceiveIncomingPushWith:for:completion:) method is never called for fileProvider type pushes. These notifications are automatically handled by the system instead.

In both your `AppDelegate` and `FileProvider` classes’ pushRegistry(_:didUpdate:for:) methods, when you receive a PKPushCredentials instance, extract the value of its token property, and send it to your server. This value is an app-specific device token. Your server uses the device token to request push notifications for this device.

```
func pushRegistry(
    _ registry: PKPushRegistry, 
    didUpdate credentials: PKPushCredentials, 
    forType type: PKPushType
) {
    let deviceToken = credentials.token
    // Send the device token to your server here.
}
```

### Send push notifications

You’re now ready to send a push notification. Start by creating a JWT; for details, see Provider Authentication Tokens. You can reuse the JWT as long as it remains valid.

Then send a POST request to the APNs server with the following values:

- The `:path` value is `/3/device/`. This token is the device token you sent to your server from your pushRegistry(_:didUpdate:for:) method.

- The `authorization` value is `bearer `. This token is your JWT.

- The `apns-topic` value is `.pushkit.fileprovider`. The bundle identifier is your app’s bundle identifier.

The POST request’s content is a JSON dictionary that specifies the container and domain for the updated content. Set the container identifier to the unique string used in the container’s itemIdentifier property. You can also use `NSFileProviderRootContainerItemIdentifier` to update the root container, or `NSFileProviderWorkingSetContainerItemIdentifier` to update the working set.

Note

When using an NSFileProviderReplicatedExtension, always set the container identifier to `NSFileProviderWorkingSetContainerItemIdentifier`. The system automatically propagates any working set changes to the user interface, without requiring you to signal individual containers. It ignores any other identifiers.

Set the domain identifier to the unique string used in the domain’s identifier property.

```
 {
     "container-identifier": ""
     "domain": ""
 }

```

For more information, see APNs Notification API.

