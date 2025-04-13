

- TV Services
-  Personalizing Your App for Each User on Apple TV 

Article

# Personalizing Your App for Each User on Apple TV

Use account-specific storage to segregate data on a multiuser system.

## Overview

Multiple people can log in to accounts on a single Apple TV, and you can set up your app so each member of a household can use it with their own Apple TV account. When a user logs in, your app can access their preferences and GameCenter and iCloud data. If your app is also available on iOS or iPadOS, a user can pick up where they left off on their personal device as well.

If your app doesn’t include the `User Management` capability, the system runs your app as the default user, instead of the current user. If you design your app with individual profiles in a single shared account, consider Mapping Apple TV users to app profiles instead.

### Access the Current User’s Data

In most cases, managing each user’s data in their Apple account provides the best user experience, but it requires some support in your app. In order to provide a personalized experience in your app, enable the `Runs as Current User` privilege in the User Management Entitlement capability. This entitlement grants your app access to data for the current user in keychain, preferences, iCloud, and Game Center.

Implement applicationWillTerminate(_:) to save data in case a user switch occurs while your app is in the foreground. Make sure you’re using applicationWillResignActive(_:) to save data whenever the user switches away from your app.

### Optimize Data Usage

When your app receives a push notification from CloudKit, use subscriptionOwnerUserRecordID to check whether the update is for the current user. If the notification is for another user on this device, you may choose to ignore the push, and get the data the next time the other user accesses your app.

## See Also

### Multiple users

Supporting Multiple Users in Your tvOS App

Store separate data for each user with the new Runs as Current User capability.

Mapping Apple TV users to app profiles

Adapt the content of your app for the current viewer by using an entitlement and simplifying sign-in flows.

class TVUserManager

An object that indicates how to store preferences for multiple people on a shared device.

