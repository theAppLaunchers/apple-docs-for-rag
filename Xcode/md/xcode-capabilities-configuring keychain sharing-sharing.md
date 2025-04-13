

- Xcode
- Capabilities
-  Configuring keychain sharing 

Article

# Configuring keychain sharing

Share keychain items between multiple apps belonging to the same developer.

## Overview

Sharing keychain items between multiple targets of the same app, or between different apps that belong to the same developer, relies on the concept of an *access group* — a collection of targets that all share a common keychain group. When a particular target wants to make a keychain item accessible to the rest of the access group, it specifies the shared keychain group when writing that item to the keychain, which can be useful for apps that need to share account credentials and other sensitive information. For more information, see Sharing access to keychain items among a collection of apps.

Before you make a keychain group accessible to your target, follow the steps in the Add a capability section of Adding capabilities to your app to add the Keychain Sharing capability to that target. For watchOS apps with separate WatchKit extensions, add the capability to the WatchKit Extension target.

If not already present, Xcode updates your target’s entitlements file to include the Keychain Access Groups Entitlement, which is an array that contains each keychain group you specify.

### Make a keychain group accessible to your target

When you want two (or more) targets to share common keychain items, make the same keychain group accessible to both by following these steps:

1.  Select your project in Xcode’s Project navigator.

2.  Select the app’s target from the Targets list.

3.  Click the Signing & Capabilities tab in the project editor.

4.  Find the Keychain Sharing capability.

5.  Click the Add (+) button below the Keychain Groups list.

6.  Double-click the inserted keychain group to edit it.

7.  Enter a name for the keychain group: either the name of an existing group that’s already in use by your other apps, or a brand new group. For new groups, use reverse DNS notation for the name.

8.  Press the Return key to save the updated keychain group.

Note

Although not visible, Xcode prepends the name of each keychain group with the `$(AppIdentifierPrefix)` build variable, which it automatically resolves at build time.

After you make a keychain group accessible to your target, you can later revoke that access by selecting the appropriate keychain group and clicking the Remove button (-) below the Keychain Groups list.

Keychain groups you specify are then available to use with the Keychain services APIs, such as SecItemAdd(_:_:) and SecItemCopyMatching(_:_:).

### Specify the default keychain group

During compilation, the system determines the canonical list of keychain groups accessible to your app by concatenating the groups you specify with the app’s unique application identifier and any App Groups you configure; the system considers the first item in that list as the default keychain group. If you omit the kSecAttrAccessGroup attribute when writing keychain items, the system automatically populates that attribute with the default keychain group, and therefore the order in which you specify your keychain groups matters.

To change the order of your keychain groups, follow these steps:

1.  In the Project navigator, Control-click your target’s entitlements file.

2.  Choose Open As \> Property List.

3.  Expand the Keychain Access Groups key.

4.  Drag the array’s nested items into your preferred order. Each item’s value is the name of a keychain group.

After making changes to the order, choose File \> Save to store those changes and cause Xcode to update the order it displays the groups in the target’s Signing & Capabilities tab.

Note

Although you can use an App Group to share keychain items, it can never be the default keychain group because the app’s unique application identifier always takes precedence.

## See Also

### Security

Configuring the hardened runtime

Protect the runtime integrity of your macOS app by restricting access to sensitive resources and preventing common exploits.

Configuring the macOS App Sandbox

Protect system resources and user data from compromised apps by restricting access to the file system, network connections, and more.

