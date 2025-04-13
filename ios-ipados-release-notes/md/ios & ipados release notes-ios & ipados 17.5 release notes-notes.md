

- iOS &amp; iPadOS Release Notes
-  iOS & iPadOS 17.5 Release Notes 

Article

# iOS & iPadOS 17.5 Release Notes

Update your apps to use new features, and test your apps against API changes.

## Overview

The iOS & iPadOS 17.5 SDK provides support to develop apps for iPhone and iPad running iOS & iPadOS 17.5. The SDK comes bundled with Xcode 15.4, available from the Mac App Store. For information on the compatibility requirements for Xcode 15.4, see Xcode 15.4 Release Notes.

### Accessibility

#### Resolved Issues

- Fixed: Accessibility AbleNet Hook+ Assistive switch MFi Accessory wired connection when connected to iPhone or iPad might not work.  (124439667)

### App Tracking Transparency

#### Resolved Issues

- Fixed: App Tracking Transparency inaccurately returns denied authorization prior to user consenting to tracking. (126589236)

### Camera and AVFoundation Capture

#### Known Issues

- `AVCaptureDeviceRotationCoordinator` returns incorrect values in Portrait and Portrait Upside Down for `videoRotationAngleForHorizonLevelCapture` and `videoRotationAngleForHorizonLevelPreview` when using the Front Camera on iPad Air 6th generation & iPad Pro 7th generation. (126887983)

### Core Motion

#### New Features

- To respect users’ privacy, apps calling CMAltimeter’s `startRelativeAltitudeUpdatesToQueue` and `stopRelativeAltitudeUpdates` are now required to include the NSMotionUsageDescription string in their plist in order to receive data.

  Apps built with SDKs prior to iOS 17.5 and watchOS 10.5 without the `NSMotionUsageDescription` string in their plists will not receive data.

  Apps built with iOS 17.5 and watchOS 10.5 or later will crash if they do not have the `NSMotionUsageDescription` string in their plist as described in CMAltimeter. (125573971)

### eSIM

#### New Features

- New Apple Universal Link for eSIM install:

  ```
   https://esimsetup.apple.com/esim_qrcode_provisioning?carddata=LPA:1$GSMA_SMDP_Address$activation_code
  ```

  Universal Links should be all lower case. Only the GSMA activation code (QR code), passed in as `carddata`, is customized for the carrier’s SM-DP+ and eSIM profile. Use the iOS user agent in web requests to determine when to offer Universal Links for eSIM, which are only be enabled on iOS 17.4 and later. (92405493)

### StoreKit

#### Resolved Issues

- Fixed an issue where the Terms of Service button on `SubscriptionStoreView` could cause a crash when tapped. (123383479)

### Wallpaper

#### Resolved Issues

- Fixed: Add New Wallpaper sheet does not load any content after restoring device. (126299569)

## See Also

### iOS &amp; iPadOS 17

iOS & iPadOS 17.6 Release Notes

Update your apps to use new features, and test your apps against API changes.

iOS & iPadOS 17.4 Release Notes

Update your apps to use new features, and test your apps against API changes.

iOS & iPadOS 17.3 Release Notes

Update your apps to use new features, and test your apps against API changes.

iOS & iPadOS 17.2 Release Notes

Update your apps to use new features, and test your apps against API changes.

iOS & iPadOS 17.1 Release Notes

Update your apps to use new features, and test your apps against API changes.

iOS & iPadOS 17 Release Notes

Update your apps to use new features, and test your apps against API changes.

