

- macOS Release Notes
-  macOS Sequoia 15.2 Release Notes 

Article

# macOS Sequoia 15.2 Release Notes

Update your apps to use new features, and test your apps against API changes.

## Overview

The macOS 15.2 SDK provides support to develop apps for Mac computers running Sequoia 15.2. The SDK comes bundled with Xcode 16.2, available from the Mac App Store. For information on the compatibility requirements for Xcode 16.2, see Xcode 16.2 Release Notes.

### Accelerate

#### Resolved Issues

- Resolved an issue impacting the accuracy of some linear algebra operations (\*lartg). These functions have been restored to their 3.9.1 implementation. (139760965) (FB15782411)

### ActivityKit

#### Resolved Issues

- Fixed: Resolved an issue where iPhone and iPad apps on Apple Silicon Macs quit unexpectedly if ActivityKit is linked. (100240357)

### Authentication Services

#### Resolved Issues

- Fixed: iPhone and iPad apps on Apple Silicon Macs might quit unexpectedly if `-[ASAuthorizationController performAutoFillAssistedRequests]` is invoked. (128153762)

### ChatGPT Integration

#### Resolved Issues

- Fixed: For devices with MDM profiles, users with anonymous restrictions are unable to sign out. (135440023)

- Fixed: Image and Document Q&A requests to ChatGPT via Siri might fail if the query doesn’t specify “photo” or “document”. (138352105)

### Kernel

#### Resolved Issues

- Fixed: Resolved an issue where running Ruby with YJIT enabled causes Mac with M4 chip to kernel panic. (139714575) (FB15774033)

### NSWritingToolsCoordinator

#### Resolved Issues

- Fixed: `NSWritingToolsCoordinator` ignores the returned attributed string from `writingToolsCoordinator(_:replaceRange:inContext:proposedText:reason:animationParameters:completion:)`. (139210266)

- Resolved an issue to properly name `NSWritingToolsCoordinator`-related enums inside an `NSWritingToolsCoordinator` extension in Swift-style: `TextUpdateReason`, `State`, `TextReplacementReason`, `ContextScope`, and `TextAnimation`. (139356801)

#### Known Issues

- `NSWritingToolsCoordinator` only supports synchronous `NSWritingToolsCoordinator.Delegate` interfaces, expecting the completion handler to be invoked without escaping the delegate methods. (136769777)

- The object does not support multiple `NSWritingToolsCoordinatorContext` elements, and supports only the first element used. Also, it does not support dynamic `decorationContainerView`. The two optional `NSWritingToolsCoordinator.Delegate` methods for multiple container support are never called. (137983691)

### ScreenCaptureKit

#### New Features

- ScreenCaptureKit is available for Catalyst applications. Developers must use the macOS 15.2 SDK or later. (104444076) (FB11957714)

- The system picking experience now surfaces additional metadata for user selected content, including details on the display, application, and window. (133085308) (FB14629093)

### SwiftUI

#### New Features

- For macOS apps linked against macOS 15.2 SDK, the `onScrollGeometryChange(for:of:action:)` modifier can be used with `List` to post geometry changes for the List-owned scroll view. (118852752)

#### Resolved Issues

- Fixed: Compiling in the Swift 6 language mode might cause an `@Entry` error due to “static property `defaultValue` is not concurrency-safe because non-‘Sendable’ type”. (133885814)

- Resolved an issue to improve performance and CPU usage when scrolling `ScrollView`s and `List`s. (137546908)

- Fixed: Views won’t accept dropped directories if UTType.directory or UTType.fileURL are not in the list of accepted content types for drop. (138158126)

### Virtualization

#### Resolved Issues

- Fixed: Installation of macOS Sequoia 15.2 Beta in VMs is not available. (137528160)

- Fixed: Resolved an issue where macOS VM guest running macOS 13.3.1 or earlier fails to boot on a host Mac with M4 chip. (139615567)

### WidgetKit

#### Resolved Issues

- Fixed: iPhone and iPad apps on Apple Silicon Macs quit unexpectedly if Live Activities API in WidgetKit are linked. (107876557)

## See Also

### macOS 15

macOS Sequoia 15.5 Beta Release Notes

Update your apps to use new features, and test your apps against API changes.

macOS Sequoia 15.4 Release Notes

Update your apps to use new features, and test your apps against API changes.

macOS Sequoia 15.3 Release Notes

Update your apps to use new features, and test your apps against API changes.

macOS Sequoia 15.1 Release Notes

Update your apps to use new features, and test your apps against API changes.

macOS Sequoia 15 Release Notes

Update your apps to use new features, and test your apps against API changes.

