

- Bundle Resources
- Entitlements
-  com.apple.developer.device-information.user-assigned-device-name 

Property List Key

# com.apple.developer.device-information.user-assigned-device-name

The entitlement for accessing the user-assigned device name instead of a generic device name.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+tvOS 16.0+visionOS 1.0+watchOS 9.0+

## Details 

Type  

boolean

## Discussion

In iOS, the *user-assigned device name* is available in the Settings app under General \> About \> Name. In iOS 15 and earlier, the name property returns this name. In iOS 16 and later, the name property returns a generic device name by default instead.

To access the user-assigned device name through the name property in iOS 16 and later, you must be assigned this entitlement. To request the entitlement, the user-assigned device name must be necessary to power a core feature of the app and must meet all of the following criteria:

- The user-assigned device name is visible to the user in your app’s UI. You must provide screenshots of this UI to request the entitlement.

- The user-assigned device name is powering a multi-device feature. Your app uses the user-assigned device name solely for functionality that’s visible to the user so that they can identify their own device, and the functionality involves interaction between multiple devices that the same user operates. For example, an app that has multi-device syncing functionality might show the user-assigned device name for each device so that the user can select between them. You must provide screenshots of this UI to request the entitlement.

- The feature using the user-assigned device name is available to all, or the vast majority of, users. The feature provides an important component of your app’s functionality to a majority of your app’s users.

- Your app doesn’t use the user-assigned device name for tracking or fingerprinting. You’re responsible for all code in your app, including any integrated SDKs. For more information about tracking, see Tracking, and for fingerprinting, see User Privacy and Data Use.

- Your app doesn’t share the user-assigned device name with any service providers or third parties other than cloud-hosting service providers. Prohibited third parties include, but aren’t limited to, third-party SDKs, ad networks, and mobile measurement partners (MMPs). There’s an exception for cloud-hosting service providers for the purposes of storage or syncing only.

If your app meets the criteria, you can request this entitlement at User-Assigned Device Name Entitlement.

Related Sessions from WWDC22

Session 10096: What’s new in privacy

Session 10068: What’s new in UIKit

