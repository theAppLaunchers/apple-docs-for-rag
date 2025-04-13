

- iOS &amp; iPadOS Release Notes
-  iOS & iPadOS 13.4 Release Notes 

Article

# iOS & iPadOS 13.4 Release Notes

Update your apps to use new features, and test your apps against API changes.

## Overview

The iOS & iPadOS 13.4 SDK provides support to develop apps for iPhone, iPad, and iPod touch devices running iOS & iPadOS 13.4. The SDK comes bundled with Xcode 11.4, available from the Mac App Store. For information on the compatibility requirements for Xcode 11.4, see Xcode 11.4 Release Notes.

### General

#### Known Issues

- To install iOS 13.4 using the Restore Image, first install Xcode 11.4.

### Keyboard

#### New Features

- QuickType Keyboard now supports predictive input for Arabic.

- QuickType Keyboard now supports Live Conversion for Japanese and Chinese (Zhuyin).

- QuickType Keyboard now supports Swiss German layout for 12.9-inch iPad layout.

#### Resolved Issues

- 12.9-inch iPad layouts for several languages now match the hardware keyboard layouts.

### Location Services

#### New Features

- When an app requests Always authorization for the first time after having previously been authorized for While Using the App, the device immediately presents the location authorization prompt. (57106235)

### Photos

#### New Features

- New keyboard shortcuts are available in Photos on iPadOS, which create quick navigation between Tabs, Search, and Create Albums. While in full-screen mode, you can also delete, duplicate, and enter Edit mode using a keyboard. (57195967)

### RealityKit

#### Known Issues

- After updating to iOS & iPadOS 13.4, you won’t be able to synchronize scenes with peers using earlier versions of RealityKit, due to a fundamental change in the physics system. If two peers running a MultipeerConnectivityService have incompatible versions, they will remain connected in the underlying MCSession, but won’t synchronize scenes. iOS & iPadOS 13.4 adds a new NetworkCompatibilityToken class so a host can avoid inviting incompatible clients to its MCSession. Please see the NetworkCompatibilityToken documentation for additional details. (59262764)

### SwiftUI

#### New Features

- When using a NavigationView with multiple columns, the navigation bar now shows a control to toggle the columns. (49074511)

- The `onDrag` and `onDrop` modifiers are now available on iOS. (49661347)

#### Resolved Issues

- safeAreaInsets in navigation and tab views now extend to the top edge as expected. If you previously used doc://com.apple.documentation/documentation/SwiftUI/AnyView/edgesIgnoringSafeArea(\_:) as a workaround, it should now be removed. (52851281)

## See Also

### iOS &amp; iPadOS 13

iOS & iPadOS 13.7 Release Notes

Update your apps to use new features, and test your apps against API changes.

iOS & iPadOS 13.6 Release Notes

Update your apps to use new features, and test your apps against API changes.

iOS & iPadOS 13.5 Release Notes

Update your apps to use new features, and test your apps against API changes.

iOS & iPadOS 13.3.1 Release Notes

Update your apps to use new features, and test your apps against API changes.

iOS & iPadOS 13.3 Release Notes

Update your apps to use new features, and test your apps against API changes.

iOS & iPadOS 13.2 Release Notes

Update your apps to use new features, and test your apps against API changes.

iOS & iPadOS 13.1 Release Notes

Update your apps to use new features, and test your apps against API changes.

iOS 13 Release Notes

Update your apps to use new features, and test your apps against API changes.

