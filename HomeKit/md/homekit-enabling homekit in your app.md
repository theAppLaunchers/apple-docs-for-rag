

- HomeKit
-  Enabling HomeKit in your app 

Article

# Enabling HomeKit in your app

Declare your app’s intention to use HomeKit, and get permission from the user to access home automation accessories.

## Overview

To access the devices in the user’s home automation network, you enable the HomeKit capability for your app. You also provide a usage description that explains to the user why the app needs access, and handle the case where the user denies access.

### Enable the HomeKit capability

To ready your app to work with HomeKit, enable the HomeKit capability for your app in Xcode. Open your project, select the app target, and choose the Signing & Capabilities pane. Then click the + button. In the window that appears, choose HomeKit.

When you enable the HomeKit capability, Xcode automatically adds the HomeKit Entitlement to your entitlements file. It also adds the corresponding feature to your App ID and links the HomeKit framework.

Important

HomeKit supports independent Apple Watch apps in watchOS 7 and later.

### Explain why your app needs access to the user’s home network

A user’s home automation network is a sensitive resource. Apps with access can collect sensor data and change the state of physical objects in the real world. To protect users, the first time your app uses the HomeKit framework—typically, when you create a HMHomeManager instance—the system prompts the user for permission.

You provide a message for this prompt called a *purpose string* or a *usage description* by setting a string value for the NSHomeKitUsageDescription that you add to your app’s Information Property List file. Find and select your project’s `Info.plist` file in Xcode’s project navigator. Modify the file using the property list editor built into Xcode:

The system automatically generates the prompt’s title, which includes the name of your app. Your usage description—in this case, “Configure accessories from Kilgo Devices, Inc.”—indicates the reason that your app needs the access.

Accurately and concisely explaining to the user why your app needs access to the home network, typically in one complete sentence, lets the user make an informed decision and improves the chances that they’ll grant access.

Important

If you don’t include a purpose string, your app crashes when you first try to use HomeKit.

### Handle permission denial gracefully

If the user grants permission, the system remembers the user’s choice and doesn’t prompt again. If the user denies permission, the access attempt that initiated the prompt and any further attempts fail. Look for a homeAccessNotAuthorized error in your completion handlers to detect this condition. Alternatively, you can inspect the home manager’s authorizationStatus property.

Be aware that even if the user allows the initial access, they can revoke permission at any time in the Settings app. Your app should handle both initial and subsequent access denials gracefully.

If home automation is a secondary function of your app—like an alarm app that plays an audible alert on the device and can also turn the house lights on when the alarm triggers—respect the user’s choice and work around denied access. For example, you can omit unavailable features from the user interface.

If your app can’t provide meaningful functionality without HomeKit access, you can display a message to the user saying so, directing them to change the privacy setting for your app to continue.

## See Also

### Essentials

HomeKit Entitlement

A Boolean value that indicates whether users of the app may manage HomeKit-compatible accessories.

NSHomeKitUsageDescription

A message that tells the user why the app is requesting access to the user’s HomeKit configuration data.

