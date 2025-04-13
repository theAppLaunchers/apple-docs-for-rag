

- Bundle Resources
- Information Property List
-  CFBundleIdentifier 

Property List Key

# CFBundleIdentifier

A unique identifier for a bundle.

iOS 2.0+iPadOS 2.0+macOS 10.0+tvOS 9.0+visionOS 1.0+watchOS 2.0+

## Details 

Name  
Bundle identifier

Type  

string

## Mentioned in 

Managing Your App’s Information Property List

## Discussion

A *bundle ID* uniquely identifies a single app throughout the system. The bundle ID string must contain only alphanumeric characters (A–Z, a–z, and 0–9), hyphens (-), and periods (.). Typically, you use a reverse-DNS format for bundle ID strings. Bundle IDs are case-insensitive.

The operating system uses the bundle ID to identify the app when applying specified preferences. Similarly, Launch Services uses the bundle ID to locate an app capable of opening a particular file. The bundle ID also validates an app’s signature.

Important

The bundle ID in the information property list must match the bundle ID you enter in App Store Connect. After you upload a build to App Store Connect, you can’t change the bundle ID or delete the associated explicit App ID in your developer account.

### watchOS Apps with Companion iOS App Considerations

For watchOS apps that have a companion iOS app in the same project, the embedded WatchKit app and WatchKit extension targets must have the same bundle ID prefix as the iOS app. The WatchKit app must have the format `[Bundle ID].watchkitapp`, and the WatchKit extension must have the format `[Bundle ID].watchkitextension`.

If you change the iOS app’s bundle ID, also change the WatchKit app’s WKCompanionAppBundleIdentifier key and the WatchKit extension’s WKAppBundleIdentifier key to match.

## See Also

### Identification

WKAppBundleIdentifier

The bundle ID of the watchOS app.

WKCompanionAppBundleIdentifier

The bundle ID of the watchOS app’s companion iOS app.

