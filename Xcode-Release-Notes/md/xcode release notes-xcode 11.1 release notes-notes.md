

- Xcode Release Notes
-  Xcode 11.1 Release Notes 

Article

# Xcode 11.1 Release Notes

Update your apps to use new features, and test your apps against API changes.

## Overview

Xcode 11.1 includes SDKs for iOS 13.1, macOS Catalina 10.15, watchOS 6, and tvOS 13. Xcode 11.1 supports on-device debugging for iOS 8 and later, tvOS 9 and later, and watchOS 2 and later. Xcode 11.1 requires a Mac running macOS Mojave 10.14.4 or later.

### General

#### Known Issues

- Xcode may fail to update from the Mac App Store after updating to macOS Catalina. (56061273)

  **Workaround**: To trigger a new download you can delete the existing Xcode.app or temporarily change the file extension so it is no longer visible to the App Store.

### Asset Catalogs

#### Known Issues

- Images in the asset catalog won’t be found at runtime when running on watchOS 4. (55395258)

### Interface Builder

#### New Features

- You can now preview your interface for the 7th generation iPad. (53957165)

#### Known Issues

- There is an issue with UITabBarController where decoding an instance from a storyboard will create some extra views at the left end of the screen. Developers may remove these by applying a workaround. (55310448)

  **Workaround**: To remove the extraneous views from Storyboard, create a subclass of a UITabBarController and add the following snippet in the class’s init(coder:) method:

  ```
  class WorkaroundTabBarController: UITabBarController {
      required init?(coder: NSCoder) {
          super.init(coder: coder)

          // This must be run immediately after the call to super.
          if tabBar.subviews.count > 1 {
              tabBar.subviews[0].isHidden = true
          }
      }
  }
  ```

#### Resolved Issues

- Fixed a crash that sometimes occurred when compiling XIB files in iOS projects that backwards deploy to iOS versions earlier than 13.0. (55271752)

### Localization

#### Known Issues

- UITableViewCell labels in storyboards and XIB files do not use localized string values from the strings file at runtime. (52839404)

### Simulator

#### Known Issues

- On macOS Catalina, iCloud Drive will crash in a loop on simulated devices running older versions of iOS. (51392951, 54282967, 54818084)

  **Workaround**: Log out of iCloud in impacted simulators to halt the crash cycle.

#### Resolved Issues

- CarPlay works on iOS 13.1 simulators. (54492162)

### Swift

#### Known Issues

- The `NEHotspotConfigurationError` enum from the Network Extension framework changed from `NS_ENUM` to `NS_ERROR_ENUM`, which can cause compiler errors in existing Swift code that uses the enum. For example, in code like this:

  ```
  let code = NEHotspotConfigurationError(rawValue: errorCode)
  ```

  You will see the error message: “error: incorrect argument label in call (have ‘rawValue:’, expected ‘\_nsError:’).” (54134493)

  **Workaround**: Replace references of `NEHotspotConfigurationError` with NEHotspotConfigurationError. For the above example, change the code to:

  ```
  let code = NEHotspotConfigurationError.Code(rawValue: errorCode)
  ```

### SwiftUI

#### Resolved Issues

- Fixed an issue with Xcode Previews where debugging a preview would no longer pin the preview, and navigating would lose the debug session. (54758098)

### Swift Packages

#### Known Issues

- If an iOS, tvOS, or watchOS app uses a Swift Package that builds a dynamic library, it cannot be submitted to the App Store. (55564324)

  **Workaround**: Modify the Package manifest to build a static library.

### watchOS

#### Known Issues

- watchOS applications built with the watchOS 6 SDK and a deployment target of watchOS 5.3 will crash on launch when run on watchOS 5.3. (55360395)

  **Workaround**: Set the `__WKEXTENSIONMAIN_LEGACY_TARGET_5_3` build setting to “legacy,” or use another deployment target instead of 5.3.

## See Also

### Xcode 11

Xcode 11.7 Release Notes

Update your apps to use new features, and test your apps against API changes.

Xcode 11.6 Release Notes

Update your apps to use new features, and test your apps against API changes.

Xcode 11.5 Release Notes

Update your apps to use new features, and test your apps against API changes.

Xcode 11.4.1 Release Notes

Update your apps to use new features, and test your apps against API changes.

Xcode 11.4 Release Notes

Update your apps to use new features, and test your apps against API changes.

Xcode 11.3.1 Release Notes

Update your apps to use new features, and test your apps against API changes

Xcode 11.3 Release Notes

Update your apps to use new features, and test your apps against API changes

Xcode 11.2.1 Release Notes

Update your apps to use new features, and test your apps against API changes.

Xcode 11.2 Release Notes

Update your apps to use new features, and test your apps against API changes.

Xcode 11 Release Notes

Update your apps to use new features, and test your apps against API changes.

