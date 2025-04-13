

- iOS &amp; iPadOS Release Notes
-  iOS 12 Release Notes 

# iOS 12 Release Notes

Update your apps to use new features, and test your apps against API changes.

## Overview

The iOS 12 SDK provides support for developing iOS apps for iPhone, iPad, or iPod touch devices running iOS 12. The SDK comes bundled with Xcode 10 available from the Mac App Store. For information about Xcode 10, see Xcode 10 Release Notes.

### App Store

#### Known Issues

- While signed in with a production account and testing with a sandbox account, attempting to fetch a new valid receipt displays a sign-in prompt for the production account with no option for switching to the sandbox account. (42862150)

  **Workaround:** For testing purposes, StoreKit calls such as making a purchase and restoring transactions will fetch a new receipt. Alternatively, sign out of the production account.

### Core Graphics

#### Known Issues

- Various Core Graphics calls have been hardened against continuing with invalid parameters. In iOS 12, these calls may now return nil or return early. (38344690)

### Core ML

#### New Features

- Support for quantized models (≤ 8-bit linear and/or lookup table)

- Support for flexible image sizes and multi-array shapes

- Batch prediction API

- Support for custom models

- Support for Create ML models (Vision Feature Print, Text Classifier, Word Tagger)

### Foundation

See Foundation Release Notes.

### HomeKit

#### Known Issues

- Inviting iOS 11 users who have multiple email addresses associated with their Apple ID to a home might not succeed. (41033550)

  **Workaround:** Send the invitation to a different email address or phone number associated with the Apple ID of the iOS 11 user.

### Maps

#### Known Issues

- Traffic data might not be displayed. (43254370)

  **Workaround:** Tap the Settings button (ⓘ) to reveal Maps Settings and toggle the Traffic switch on.

### MediaPlayer Framework

#### Known Issues

- When perform(queueTransaction:completionHandler:) is called on applicationQueuePlayer to modify the position of a song, the queue returns unchanged. (39401344)

### Networking

#### New Features

- The URLSession HTTP/2 implementation supports HTTP/2 connection reuse per RFC 7540 Section 9.1.1. This requires an HTTP/2 server to present a certificate which covers more than one server hostname. The certificate may use the Subject Alternative Name extension or wild-carded domain names. In addition, URLSession requires name resolution to resolve the different hostnames to the same IP address. URLSession may reuse HTTP/2 connections across different domain names when these conditions are satisfied. (37507838)

#### Deprecations

- FTP and File URL schemes for Proxy Automatic Configuration (PAC) are deprecated. HTTP and HTTPS are the only supported URL schemes for PAC. This affects all PAC configurations including, but not limited to, configurations set via Settings, System Preferences, profiles, and URLSession APIs such as connectionProxyDictionary, and CFNetworkExecuteProxyAutoConfigurationURL(_:_:_:_:). (37811761)

### Phone and FaceTime

#### Known Issues

- Group FaceTime has been removed from the initial release of iOS 12 and will ship in a future software update later this fall.

- In iOS 12, Camera Effects in Messages is available only on iPhone SE and iPhone 6s or later and is unavailable on iPad. Camera Effects in FaceTime is available only on iPhone 7 or later and is unavailable on iPad.

- Wi-Fi calls might end unexpectedly when transitioning from Wi-Fi to cellular while on the T-Mobile network. (39251828)

### Screen Time

#### Known Issues

- The start and stop times for Downtime might change unexpectedly if they were configured prior to installing iOS 12 beta 9. (43393555)

  **Workaround:** Update all devices associated with the iCloud account to the release version of iOS 12 and reset the start and stop times for Downtime.

- After updating to iOS 12, parents should change the Screen Time passcode to prevent children from signing out of iCloud or changing the system time. (42879250)

- “Picked Up Phone” statistics might be inflated due to data syncing from other devices signed into the same iCloud account. (39917173)

### Siri

#### Known Issues

- When using doc://com.apple.documentation/documentation/SiriKit/INUIAddVoiceShortcutButton, the “Add to Siri” and “Added to Siri” button text isn’t localized. (43251696)

  **Workaround:** To localize “Add to Siri” and “Added to Siri” button text, include localizations for this text in the strings files of your app bundle.

- While multiple ride-sharing apps are installed, Siri might open the app instead of providing an ETA or location when asked. (42324032)

  **Workaround:** Ask Siri for the ETA or location again.

- Siri Shortcuts might not work if a device is locked. (41307405)

- Siri Suggestions for Shortcuts are enabled on iPhone 6s or later, iPad Pro, iPad (5th generation or later), iPad Air 2, and iPad mini 4. (40669231)

### UIKit

#### Known Issues

- You might encounter issues with systemLayoutSizeFitting(_:) when using a UICollectionViewCell subclass that requires updateConstraints(). (42138227)

  **Workaround:** Don’t call the cell’s setNeedsUpdateConstraints() method unless you need to support live constraint changes. If you need to support live constraint changes, call updateConstraintsIfNeeded() before calling systemLayoutSizeFitting(_:).

### USB Accessories

#### New Features

- To improve security, iOS 12 may require you unlock your passcode-protected iPhone, iPad, or iPod touch in order to connect it to a Mac, PC, or USB accessory.

- If you use iPod Accessory Protocol (iAP) USB accessories over the Lightning connector (such as CarPlay, assistive devices, charging accessories, or storage carts) or you connect to a Mac or PC you might need to unlock your device to recognize the accessory. If you don’t unlock your device, it won’t communicate with the accessory or computer, and it won’t charge. Note that you don’t need to unlock your device to charge using an Apple USB power adapter.

- If a USB accessory isn’t recognized after you unlock your device, disconnect it, unlock your device, and reconnect the accessory.

- If you normally use a USB assistive device to enter your passcode, you may allow it to communicate with your device while it is locked by enabling “USB Accessories” in Settings \> Face ID/Touch ID & Passcode.

### Xcode

#### Known Issues

- When using Messages in the iOS Simulator, a message might not be delivered from User A to User B. (40916530)

  **Workaround:** Send a message from User B to User A.

## Topics

### Foundation

Foundation Release Notes

Update your apps to use new features, and test your apps against API changes.

## See Also

### iOS 12

iOS 12.4 Release Notes

Update your apps to use new features, and test your apps against API changes.

iOS 12.3 Release Notes

Update your apps to use new features, and test your apps against API changes.

iOS 12.2 Release Notes

Update your apps to use new features, and test your apps against API changes.

iOS 12.1.3 Release Notes

Update your apps to use new features, and test your apps against API changes.

iOS 12.1.1 Release Notes

Update your apps to use new features, and test your apps against API changes.

iOS 12.1 Release Notes

Update your apps to use new features, and test your apps against API changes.

