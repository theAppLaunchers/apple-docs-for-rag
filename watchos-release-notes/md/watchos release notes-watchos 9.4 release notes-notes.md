

- watchOS Release Notes
-  watchOS 9.4 Release Notes 

Article

# watchOS 9.4 Release Notes

Update your apps to use new features, and test your apps against API changes.

## Overview

The watchOS 9.4 SDK provides support to develop watchOS apps for Apple Watch devices running watchOS 9.4. The SDK comes bundled with Xcode 14.3, available from the Mac App Store. For information on the compatibility requirements for Xcode 14.3, see Xcode 14.3 Release Notes.

### General

#### Resolved Issues

- Fixed: Apple Watch Series 6 (44mm) now estimates its maximum battery capacity more accurately. (105740118)

### Medications

#### Known Issues

- Users who were previously on 9.2.1 build may experience issues of missing Medication Schedule on Watch, or Medication dose logged on Watch not appearing on Phone (106108448)

  **Workaround:** 1) On companion iPhone: remove the affected medication schedule and re-add it. Or 2) On affected Watch: erase and reinstall as new device any releases after 9.2.1

### SwiftUI

#### Resolved Issues

- Fixed: `ScrollView` has improved support for right to left languages by default. If you have a `ScrollView` that shouldn’t change its behavior in right to left languages, use the `.environment(\.layoutDirection, .leftToRight)` modifier to ensure the `ScrollView` always sees a left to right layout direction. (65108729)

- Fixed: Presentations in SwiftUI using the ‘sheet’ or ‘fullScreenCover’ modifier can now be dynamically presented again while a dismiss animation is in progress. Previously, attempting to present again in this case would do nothing.

  Note: A data race in app code that was previously ignored might cause a sheet to be presented again with this change. If this happens, check that your state isn’t triggering a new presentation. (101487810)

## See Also

### watchOS 9

watchOS 9.6 Release Notes

Update your apps to use new features, and test your apps against API changes.

watchOS 9.5 Release Notes

Update your apps to use new features, and test your apps against API changes.

watchOS 9.3 Release Notes

Update your apps to use new features, and test your apps against API changes.

watchOS 9.2 Release Notes

Update your apps to use new features, and test your apps against API changes.

watchOS 9.1 Release Notes

Update your apps to use new features, and test your apps against API changes.

watchOS 9 Release Notes

Update your apps to use new features, and test your apps against API changes.

