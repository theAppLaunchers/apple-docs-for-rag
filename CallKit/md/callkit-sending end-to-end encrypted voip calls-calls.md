

- CallKit
-  Sending End-to-End Encrypted VoIP Calls 

Article

# Sending End-to-End Encrypted VoIP Calls

Initiate VoIP calls when your server can’t determine whether an outgoing notification is a request for a VoIP call due to metadata encryption.

## Overview

If your app can send multiple types of end-to-end encrypted (E2EE) data—for example both text messages and voice over IP (VoIP) calls—send the encrypted content as a remote notification. Then, on the receiving device, use a notification service extension to decrypt the incoming content. If the content represents a VoIP call, pass the call information to CallKit by calling the reportNewIncomingVoIPPushPayload(_:completion:) method. The system launches your app before passing the message on to CallKit. CallKit then displays the call to the user. It uses the same interface as the Phone app, giving your app a more native look and feel. It also responds appropriately to system-level behaviors such as Do Not Disturb.

Important

Only use this approach when your server can’t determine whether an outgoing notification is a request for a VoIP call or some other data (such as a text message) due to metadata encryption. If your server knows that the outgoing content is a VoIP call, send a voIP push notification instead. For more information, see PushKit.

### Configure your App to Process Multiple Types of E2EE Data

The workflow for receiving, decrypting, and processing multiple types of E2EE data involves several different components working together. To set up these systems:

- Request permission to receive remote notifications through the User Notifications framework. See Asking permission to use notifications.

- Register for VoIP calls using PushKit. See Supporting PushKit Notifications in Your App.

- Add a Notification Service Extension target to your app. See Modifying content in newly delivered notifications.

- Add the `com.apple.developer.usernotifications.filtering` entitlement to the Notification Service Extension target’s entitlements file. To apply for this entitlement, see Notification Service Extension Filtering Entitlement Request.

### Send the VoIP Request

To send an E2EE VoIP message:

1.  A user initiates a VoIP call on their app. Their app then sends an encrypted VoIP call request to your server.

2.  Your server sends the encrypted data to the receiver’s device using a regular remote notification. Be sure to set the `apns-push-type` header field to `alert`. For more information, see Sending notification requests to APNs.

3.  On the receiver’s device, the notification service extension processes the incoming notification and decrypts it. If it’s an incoming VoIP call, the extension calls reportNewIncomingVoIPPushPayload(_:completion:) to initiate the call. It then silences the push notification (see com.apple.developer.usernotifications.filtering).

4.  Finally, the system launches the extension’s containing app and calls the pushRegistry(_:didReceiveIncomingPushWith:for:completion:) method. From this point, the app handles the call just like any incoming VoIP call. Specifically, your pushRegistry(_:didReceiveIncomingPushWith:for:completion:) implementation must call the reportNewIncomingCall(with:update:completion:) method to report the call. CallKit then presents the incoming call to the user.

## See Also

### Outgoing calls

class CXCallController

A programmatic interface for interacting with and observing calls.

class CXTransaction

An object that contains zero or more action objects for a call controller to perform.

class CXStartCallAction

An encapsulation of the act of initiating an outgoing call.

