

- watchOS apps
- Notifications
-  Grouping notifications 

Article

# Grouping notifications

Organize notifications into threads.

## Overview

The system groups related notifications together in the Notification Center. You can control how watchOS groups your app’s notifications by adding a thread identifier.

### Set the thread identifier

The system automatically groups notifications with the same category and thread ID as they arrive. For local notifications, set the content’s threadIdentifier property. For remote notifications, use the `thread-id` key.

```
let myPOICategory = "NearbyPlaceOfInterestCategoryIdentifier"
let myPOIThread = "NearbyPlaceOfInterestThreadIdentifier"

// Create the local notification's content.
let content = UNMutableNotificationContent()
content.title = "Grand Canyon"
content.body = "You are within 50 miles of the Grand Canyon"

// Enable grouping by adding a thread identifier.
content.threadIdentifier = myPOIThread

// Then create the request for the notification.
let request = UNNotificationRequest(identifier: myPOICategory,
                                    content: content)
```

### Display groups in custom interfaces

Additionally, if you provide a custom long-look interface, it can respond to grouped notifications, displaying content from multiple notifications within a single interface. If a custom notification interface is on screen and a new notification with a matching category and thread ID arrives, the system calls your notification controller’s didReceive(_:) method again. Your implementation must be prepared to append the incoming content to the existing interface. For example, if your custom interface displays the content in a table view, you can add a new row for the incoming content.

## See Also

### Customizing the user experience

Taking advantage of notification forwarding

Deliver notifications to the user’s iPhone or Apple Watch.

Customizing your long-look interface

Create custom interfaces for your watchOS app’s notifications.

Adding actions to notifications on watchOS

Provide a set of responses to a notification.

