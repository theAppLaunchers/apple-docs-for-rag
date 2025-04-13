

- watchOS apps
- Notifications
-  Testing custom notification interfaces 

Article

# Testing custom notification interfaces

Test your notification interfaces on watchOS using a notification scheme and payload file.

## Overview

When you’re ready to test your dynamic interface in the simulator, create a custom build scheme for running your notification interface. To configure the scheme, specify the JSON data file containing the test data you want delivered to your interface.

When you create a new WatchKit App project or add a WatchKit App template to an existing project, Xcode adds notification scenes by default. This includes setting up the scheme and providing `PushNotificationPayload.apns`, a file with test JSON data. This file contains most of the keys you need to simulate a remote notification; however, you can add more keys.

If Xcode added the notification scenes for you, just modify the `PushNotificationPayload.apns` file so that it contains test data appropriate for your app. If you added the notification scenes yourself, you need to set up the scheme and payload file as well.

### Add a scheme

As you add notifications to your app, you also need to add a scheme to test the notifications. To test multiple notification categories, add a scheme for each category.

To add a scheme, click the current scheme in Xcode’s toolbar, and select New Scheme.

In the New Scheme sheet, set the Target to your WatchKit app, and give the scheme a meaningful name.

Click OK. Xcode adds and selects the scheme. To configure the new scheme, click the current scheme again, and select Edit Scheme.

In the Edit Scheme sheet, set the Watch Interface to Dynamic Notification. Also set the Notification Payload to the desired payload file. Then click Close.

### Create a payload file

To test notification interfaces, you can specify a payload file that contains the test data for your notification. Payload files are text files with an `.apns` extension. They contain the JSON payload data for your notification. For example, a simple payload file includes the following.

```
```

Running a notification scheme sends the corresponding payload to the watch. You can also trigger a notification by dragging and dropping a payload file onto either the iPhone or Apple Watch simulator. In this case, you must set the “Simulator Target Bundle” to the correct target’s bundle ID. Also, your app must have already requested permission to receive notifications on that device. Finally, the system doesn’t necessarily deliver the notification immediately. You may have a delay of up to a minute before the notification appears.

To add a new payload file:

1.  Select File \> New \> File.

2.  In the file template sheet, make sure the iOS tab is selected, then scroll down to the Apple Watch group. Select the Notification Simulation File template and click Next.

3.  Name the payload file and click Create.

The template creates a new file with the default JSON payload data. To use this file, select it in the Scheme editor when configuring the build scheme for a notification interface. You can include multiple payload files in your project and either change the build scheme or create multiple build schemes to simplify your testing.

### Edit the JSON payload

The system packages most of the JSON data into a dictionary and delivers it to your app at runtime. You can modify the contents of the payload file to match the actual content of typical notifications sent to your app. At a minimum, change the value of the `category` key to match the name of your notification category. For more information on creating a notification payload, see Generating a remote notification.

Note that the payload file includes a WatchKit Simulator Actions key. This key isn’t part of a normal notification’s payload. The Apple Watch simulator doesn’t have access to your iOS app’s registered actions, so you must define the actions in the payload file. The WatchKit Simulator Actions key contains an array of dictionaries, each of which represents an action button.

Each dictionary can contain the following keys:

`title`  
(Required) The title of the action button.

`identifier`  
(Required) A string that identifies the action selected by the user. When the user taps the button, the system calls your notification center delegate’s userNotificationCenter(_:didReceive:withCompletionHandler:) method. The system assigns the value of this key to the actionIdentifier property of the UNNotificationResponse object passed to this method.

`behavior`  
(Optional) The only valid value for this key is the string `textInput`. If this key is present, the resulting button triggers text input.

`destructive`  
(Optional) The value `1` or `0`, where `1` causes the resulting button to be rendered in a way that indicates it performs a destructive action. The value `0` causes the button to be rendered normally.

`background`  
(Optional) The value `1` or `0`, where `1` causes the button to launch the app in the background.

### Send test notifications to the watch

Because the system automatically determines whether to deliver notifications to Apple Watch, when testing on the device, you may need to set the devices’ states to make sure the system routes the notification to Apple Watch as expected. To test your notification interfaces while the device isn’t on your wrist:

- Disable Wrist Detection on Apple Watch. You can set this in the Watch app on the companion iPhone or in the Settings app on the watch. The option is under Passcode \> Wrist Detection.

- Make sure your Apple Watch isn’t on a charger.

- Make sure to lock your iPhone.

