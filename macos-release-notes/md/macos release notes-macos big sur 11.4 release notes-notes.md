

- macOS Release Notes
-  macOS Big Sur 11.4 Release Notes 

Article

# macOS Big Sur 11.4 Release Notes

Update your apps to use new features, and test your apps against API changes.

## Overview

To develop apps for macOS Big Sur 11.4, build your apps against the macOS 11.3 SDK or later. The SDK comes bundled with Xcode 12.5, available from the Mac App Store. For information on the compatibility requirements for Xcode 12.5, see Xcode 12.5 Release Notes.

### Displays

#### New Features

- You can now use graphics cards based on the AMD Navi RDNA2 architecture (6800, 6800XT and 6900XT). (73709953)

### Xcode

#### Deprecations

- Don’t use the iOS MinimumOSVersion information property list key to declare the minimum release of macOS in which your app runs. Use LSMinimumSystemVersion instead. (73890473)

  - Future releases of macOS ignore the `MinimumOSVersion` key in Mac apps, including apps built with Mac Catalyst.

  - Future releases of macOS use the `LSMinimumSystemVersion` key in iOS apps built with Xcode 12.5 or later. If an iOS app doesn’t include an `LSMinimumSystemVersion` key, future releases of macOS compare the app’s `MinimumOSVersion` with the version of its Mac Catalyst runtime to determine compatibility.

## See Also

### macOS 11

macOS Big Sur 11.5 Release Notes

Update your apps to use new features, and test your apps against API changes.

macOS Big Sur 11.3 Release Notes

Update your apps to use new features, and test your apps against API changes.

macOS Big Sur 11.2 Release Notes

Update your apps to use new features, and test your apps against API changes.

macOS Big Sur 11.1 Release Notes

Update your apps to use new features, and test your apps against API changes.

macOS Big Sur 11.0.1 Release Notes

Update your apps to use new features, and test your apps against API changes.

macOS Big Sur 11.0.1 Universal Apps Release Notes

Update your apps to support Macs with Apple silicon.

macOS Big Sur 11.0.1 iOS & iPadOS Apps on Mac Release Notes

Considerations for running iPhone and iPad apps on Macs with Apple silicon.

