

- User Notifications
-  Modifying content in newly delivered notifications 

Article

# Modifying content in newly delivered notifications

Modify the payload of a remote notification before it’s displayed on the user’s iOS device.

## Overview

You may want to modify the content of a remote notification on a user’s iOS device if you need to:

- Decrypt data sent in an encrypted format.

- Download images or other media attachments whose size would exceed the maximum payload size.

- Update the notification’s content, perhaps by incorporating data from the user’s device.

Modifying a remote notification requires a notification service app extension, which you include inside your iOS app bundle. The app extension receives the contents of your remote notifications before the system displays them to the user, giving you time to update the notification payload. You control which notifications your extension handles.

Important

Notification service app extensions only operate on remote notifications configured in the system to display an alert to the user. If alerts are disabled for your app, or if the payload specifies only the playing of a sound or the badging of an icon, the extension isn’t employed.

### Add a service app extension to your project

A notification service app extension ships as a separate bundle inside your iOS app. To add this extension to your app:

1.  Select File \> New \> Target in Xcode.

2.  Select the Notification Service Extension target from the iOS \> Application section.

3.  Click Next.

4.  Specify a name and other configuration details for your app extension.

5.  Click Finish.

### Implement your extension’s handler methods

The notification service app extension template provided by Xcode includes a default implementation for you to modify.

- Use the didReceive(_:withContentHandler:) method to create a new UNMutableNotificationContent object with the updated content.

- Use the serviceExtensionTimeWillExpire() method to terminate any payload-modification tasks that are still running.

Your didReceive(_:withContentHandler:) method has only about 30 seconds to modify the payload and call the provided completion handler. If your code takes longer than that, the system calls the serviceExtensionTimeWillExpire() method, at which point you must return whatever you can to the system immediately. If you fail to call the completion handler from either method, the system displays the original contents of the notification.

Listing 1 shows an implementation of the UNNotificationServiceExtension object that decrypts the contents of a secret message delivered using a remote notification. The didReceive(_:withContentHandler:) method decrypts the data and returns a modified version of the notification’s content if it’s successful. If it’s unsuccessful, or if time expires, the extension returns content indicating that the data is still encrypted.

Listing 1. Decrypting data contained in a remote notification

```
// Storage for the completion handler and content.
var contentHandler: ((UNNotificationContent) -> Void)?
var bestAttemptContent: UNMutableNotificationContent?
// Modify the payload contents.
override func didReceive(_ request: UNNotificationRequest,
         withContentHandler contentHandler: 
         @escaping (UNNotificationContent) -> Void) {
   self.contentHandler = contentHandler
   self.bestAttemptContent = (request.content.mutableCopy() 
         as? UNMutableNotificationContent)

   // Try to decode the encrypted message data.
   let encryptedData = bestAttemptContent?.userInfo["ENCRYPTED_DATA"]
   if let bestAttemptContent = bestAttemptContent {
      if let data = encryptedData as? String {
         let decryptedMessage = self.decrypt(data: data)
        bestAttemptContent.body = decryptedMessage
      }
      else {
         bestAttemptContent.body = "(Encrypted)"
      }

      // Always call the completion handler when done.      
      contentHandler(bestAttemptContent)
   }
}

// Return something before time expires.
override func serviceExtensionTimeWillExpire() {
   if let contentHandler = contentHandler, 
      let bestAttemptContent = bestAttemptContent {

      // Mark the message as still encrypted.   
      bestAttemptContent.subtitle = "(Encrypted)"
      bestAttemptContent.body = ""
      contentHandler(bestAttemptContent)
   }
}
```

### Configure the payload for the remote notification

The system executes your notification service app extension only when a remote notification’s payload contains the following information:

- The payload must include the `mutable-content` key with a value of `1`.

- The payload must include an `alert` dictionary with title, subtitle, or body information.

Listing 2 shows the JSON data for a notification payload containing encrypted data. The `mutable-content` flag is set so that the user’s device knows to run the corresponding service app extension, the code for which is shown in .

Listing 2. Specifying the remote notification payload

```
```

## See Also

### Notification service app extension

class UNNotificationServiceExtension

An object that modifies the content of a remote notification before it’s delivered to the user.

