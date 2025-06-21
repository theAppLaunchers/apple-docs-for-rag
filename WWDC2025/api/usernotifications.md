Framework

# User Notifications

Push user-facing notifications to the user’s device from a server, or generate them locally from your app.

iOS 10.0+iPadOS 10.0+Mac Catalyst 13.0+macOS 10.14+tvOS 10.0+visionOS 1.0+watchOS 3.0+

## [Overview](/documentation/UserNotifications#overview)

User-facing notifications communicate important information to users of your app, regardless of whether your app is running on the user’s device. For example, a sports app can let the user know when their favorite team scores. Notifications can also tell your app to download information and update its interface. Notifications can display an alert, play a sound, or badge the app’s icon.

![A notification interface displayed on the lock screen and on the Home screen of an iOS device.](https://docs-assets.developer.apple.com/published/77222b2547b6bca98259cae756936c96/media-4182210%402x.png)

You can generate notifications locally from your app or remotely from a server that you manage. For _local notifications_, the app creates the notification content and specifies a condition, like a time or location, that triggers the delivery of the notification. For _remote notifications_, your company’s server generates push notifications, and Apple Push Notification service (APNs) handles the delivery of those notifications to the user’s devices.

Use this framework to do the following:

*   Define the types of notifications that your app supports.
    
*   Define any custom actions associated with your notification types.
    
*   Schedule local notifications for delivery.
    
*   Process already delivered notifications.
    
*   Respond to user-selected actions.
    

The system makes every attempt to deliver local and remote notifications in a timely manner, but delivery isn’t guaranteed. The PushKit framework offers a more timely delivery mechanism for specific types of notifications, such as those VoIP and watchOS complications use. For more information, see [PushKit](/documentation/PushKit).

For webpages in Safari version 16.0 and higher, generate remote notifications from a server that you manage using [Push API](https://www.w3.org/TR/push-api/) code that works in Safari and other browsers.

Note

Siri can provide suggestions to users in search, News, Safari, and other apps using on-device information that your app contributes through the Notifications API. Users can change this functionality to allow at any time through Siri and Search settings for your app.

For design guidance, see [Human Interface Guidelines > Notifications](https://developer.apple.com/design/human-interface-guidelines/ios/system-capabilities/notifications/).

## [Topics](/documentation/UserNotifications#topics)

### [Essentials](/documentation/UserNotifications#Essentials)

[

User Notifications updates](/documentation/Updates/UserNotifications)

Learn about important changes in User Notifications.

[

Asking permission to use notifications](/documentation/usernotifications/asking-permission-to-use-notifications)

Request permission to display alerts, play sounds, or badge the app’s icon in response to a notification.

### [Notification management](/documentation/UserNotifications#Notification-management)

```swift
```swift
```swift
```swift
class UNUserNotificationCenter
```
```

The central object for managing notification-related activities for your app or app extension.
```
```swift
```swift
```swift
protocol UNUserNotificationCenterDelegate
```
```

An interface for processing incoming notifications and responding to notification actions.
```
```swift
```swift
```swift
class UNNotificationSettings
```
```

The object for managing notification-related settings and the authorization status of your app.
```
```

### [Remote notifications](/documentation/UserNotifications#Remote-notifications)

Generate notifications from your company’s servers, and deliver those notifications using APNs.

[

API Reference

Setting up a remote notification server](/documentation/usernotifications/setting-up-a-remote-notification-server)

Generate notifications and push them to user devices.

[

Sending push notifications using command-line tools](/documentation/usernotifications/sending-push-notifications-using-command-line-tools)

Use basic macOS command-line tools to send push notifications to Apple Push Notification service (APNs).

[

Testing notifications using the Push Notification Console](/documentation/usernotifications/testing-notifications-using-the-push-notification-console)

Send test notifications and access delivery logs to test your app’s integration with Apple Push Notification service (APNs).

### [Notification requests](/documentation/UserNotifications#Notification-requests)

Create delivery requests for local notifications, and access the content of delivered local and remote notifications.

[

API Reference

Scheduling a notification locally from your app](/documentation/usernotifications/scheduling-a-notification-locally-from-your-app)

Create and schedule notifications from your app when you want to get the user’s attention.

```swift
```swift
```swift
class UNNotificationRequest
```
```

A request to schedule a local notification, which includes the content of the notification and the trigger conditions for delivery.
```
```swift
```swift
```swift
class UNNotification
```
```

The data for a local or remote notification the system delivers to your app.
```

### [Push notifications in safari](/documentation/UserNotifications#Push-notifications-in-safari)

[

Sending web push notifications in web apps and browsers](/documentation/usernotifications/sending-web-push-notifications-in-web-apps-and-browsers)

Update your web server and website to send push notifications that work in Safari, other browsers, and web apps, following cross-browser standards.

### [Notification content](/documentation/UserNotifications#Notification-content)

Modify and examine the payload of a notification.

[

Implementing communication notifications](/documentation/usernotifications/implementing-communication-notifications)

Configure and display your app’s communication notifications by using intents.

```swift
```swift
```swift
protocol UNNotificationContentProviding
```
```

A protocol the system uses to provide context relevant to user notifications.
```
```swift
```swift
```swift
class UNNotificationActionIcon
```
```

An icon associated with an action.
```
```swift
```swift
```swift
class UNMutableNotificationContent
```
```

The editable content for a notification.
```
```swift
```swift
```swift
class UNNotificationContent
```
```

The uneditable content of a notification.
```
```swift
```swift
```swift
class UNNotificationAttachment
```
```

A media file associated with a notification.
```
```swift
```swift
```swift
class UNNotificationSound
```
```

The sound played upon delivery of a notification.
```
```swift
```swift
```swift
struct UNNotificationSoundName
```
```

A string providing the name of a sound file.
```

### [Triggers](/documentation/UserNotifications#Triggers)

Define the trigger conditions for delivering notifications. Detect when a remote notification was delivered from APNs.

```swift
```swift
```swift
class UNCalendarNotificationTrigger
```
```

A trigger condition that causes a notification the system delivers at a specific date and time.
```
```swift
```swift
```swift
class UNTimeIntervalNotificationTrigger
```
```

A trigger condition that causes the system to deliver a notification after the amount of time you specify elapses.
```
```swift
```swift
```swift
class UNLocationNotificationTrigger
```
```

A trigger condition that causes the system to deliver a notification when the user’s device enters or exits a geographic region you specify.
```
```swift
```swift
```swift
class UNPushNotificationTrigger
```
```

A trigger condition that indicates Apple Push Notification Service (APNs) has sent the notification.
```
```swift
```swift
```swift
class UNNotificationTrigger
```
```

The common behavior for subclasses that trigger the delivery of a local or remote notification.
```

### [Notification categories and user actions](/documentation/UserNotifications#Notification-categories-and-user-actions)

Define the types of notifications that your app supports, and define how users can respond.

[

Declaring your actionable notification types](/documentation/usernotifications/declaring-your-actionable-notification-types)

Differentiate your notifications and add action buttons to the notification interface.

```swift
```swift
```swift
class UNNotificationCategory
```
```

A type of notification your app supports and the custom actions that the system displays.
```
```swift
```swift
```swift
class UNNotificationAction
```
```

A task your app performs in response to a notification that the system delivers.
```
```swift
```swift
```swift
class UNTextInputNotificationAction
```
```

An action that accepts user-typed text.
```

### [Notification responses](/documentation/UserNotifications#Notification-responses)

[

Handling notifications and notification-related actions](/documentation/usernotifications/handling-notifications-and-notification-related-actions)

Respond to user interactions with the system’s notification interfaces, including handling your app’s custom actions.

```swift
```swift
```swift
class UNNotificationResponse
```
```

The user’s response to an actionable notification.
```
```swift
```swift
```swift
class UNTextInputNotificationResponse
```
```

The user’s response to an actionable notification, including any custom text that the user typed or dictated.
```

### [Notification service app extension](/documentation/UserNotifications#Notification-service-app-extension)

Use a notification service app extension to modify the content of a notification before it’s delivered to your app.

[

Modifying content in newly delivered notifications](/documentation/usernotifications/modifying-content-in-newly-delivered-notifications)

Modify the payload of a remote notification before it’s displayed on the user’s iOS device.

```swift
```swift
```swift
class UNNotificationServiceExtension
```
```

An object that modifies the content of a remote notification before it’s delivered to the user.
```

### [Entitlements](/documentation/UserNotifications#Entitlements)

[`APS Environment Entitlement`](/documentation/BundleResources/Entitlements/aps-environment)

The environment for push notifications.

[`APS Environment (macOS) Entitlement`](/documentation/BundleResources/Entitlements/com.apple.developer.aps-environment)

The environment for push notifications in macOS apps.

### [Sample code](/documentation/UserNotifications#Sample-code)

[

Handling Communication Notifications and Focus Status Updates](/documentation/usernotifications/handling-communication-notifications-and-focus-status-updates)

Create a richer calling and messaging experience in your app by implementing communication notifications and Focus status updates.

[

Implementing Alert Push Notifications](/documentation/usernotifications/implementing-alert-push-notifications)

Add visible alert notifications to your app by using the UserNotifications framework.

[

Implementing Background Push Notifications](/documentation/usernotifications/implementing-background-push-notifications)

Add background notifications to your app by using the UserNotifications framework.

### [Reference](/documentation/UserNotifications#Reference)

[

API Reference

UserNotifications Constants](/documentation/usernotifications/usernotifications-constants)

### [Classes](/documentation/UserNotifications#Classes)

```swift
```swift
```swift
```swift
class UNNotificationAttributedMessageContext
```
```
```
```