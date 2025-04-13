

- iOS &amp; iPadOS Release Notes
-  iOS & iPadOS 14 Release Notes 

Article

# iOS & iPadOS 14 Release Notes

Update your apps to use new features, and test your apps against API changes.

## Overview

The iOS & iPadOS 14 SDK provides support to develop apps for iPhone, iPad, and iPod touch devices running iOS & iPadOS 14. The SDK comes bundled with Xcode 12, available from the Mac App Store. For information on the compatibility requirements for Xcode 12, see Xcode 12 Release Notes.

### General

#### Known Issues

Important

Updating to iOS & iPadOS 14 from previous versions of iOS & iPadOS might take significantly longer than expected. Data loss could occur if the update is interrupted. (59101197)

- macOS Big Sur 11 beta 6 or Xcode 12 might be required to sync or update devices running iOS & iPadOS 14 or later.

- macOS Big Sur 11 beta 6 is required to use the restore images for iOS & iPadOS 14 or later.

### App Clips

#### New Features

- You can now use Settings \> Developer Settings to test an App Clip card. (64787288)

### App Store

#### Known Issues

- Avoid calling the presentCodeRedemptionSheet() API until you’re able to create supported codes. (59351258)

#### New Features

- SKOverlay enables downloading an app without having to leave the current app. The overlay can also be tapped to view the app in the App Store. In an App Clip, `SKOverlay` enables users to download the corresponding full app from within the App Clip. (56886149)

- You can now manage subscriptions, test upgrades, downgrades, and cancellations, as well as reset the introductory offer eligibility for a test account, by tapping on your sandbox account in Settings. (57248908)

- The `userInfo` parameter can now be passed to Account Authentication Modification Extensions during in-app upgrades. (64128404)

### AVFoundation

#### New Features

- A new feature in `AVAudioSession` allows clients to request stereo polar patterns from the built-in mic. Clients choosing a stereo polar pattern must call a new method of `AVAudioSession` to specify the stereo input orientation. For more information, see AVAudioSession (58584572)

### Core Haptics

#### Known Issues

- CHHapticEngine vended through the Game Controller framework (GCDeviceHaptics) don’t support CHHapticAdvancedPatternPlayer and an error is returned on advanced player creation.

- audioCustom and audioContinuous events sent to CHHapticEngine vended through the Game Controller framework (GCDeviceHaptics) are silently ignored. (65163373)

- The creation of CHHapticEngine via class initializers is available only in iOS. For other platforms, access these engines via GCController. (65481931)

### Core ML

#### Deprecations

- The default initializer on the auto-generated model interface has been deprecated in favor of `init(configuration:)`. Use `init(configuration:)` or the newly introduced `.load()` method and handle model load errors as appropriate. (64432588)

### Fonts

#### Known Issues

- Beginning in iOS & iPadOS 14, fonts installed using configuration profiles are only available to apps supporting the font APIs and entitlements introduced in iOS & iPadOS 13. If your app provides a custom font-selection interface, it can no longer access fonts installed via configuration profiles. For reference, see the WWDC 2019 Session Font Management and Text Scaling (55317428)

### HealthKit

#### New Features

- New data types are available to track mobility metrics including walking speed, step length, double-support percentage, and more. (56387364)

- HKElectrocardiogram enables reading electrocardiogram voltage data and classifications recorded by Apple Watch. (56396806)

### Home Screen

#### Known Issues

- Spotlight might not appear as expected. (64121178)

  **Workaround:** Restart your device.

### Key-Value Observing

#### New Features

- Key-Value Observation removal facilities now employ deterministic bookkeeping methods. Cases that would have produced hard-to-diagnose crashes, especially those where KVO signals problems accessing deallocated observer pointers or observers associated with incorrect objects, now produce an exception that pinpoints which observed object needs a missed removeObserver(_:) call, and by which observers. This exception was previously thrown as ‘best effort’ when KVO could detect the problem; the new deterministic bookkeeping allows it to be thrown for all cases where `removeObserver(_:)` is needed.

  The improved determinism also allows improved Swift API handling. Instances of NSKeyValueObservation, produced by the Swift `NSObject.observe(_:changeHandler:)` method, take advantage of integration with this bookkeeping so they now invalidate automatically when the observed object is released, regardless of how the object implements its KVO behavior. This applies to all usage of this API in macOS 11 Big Sur beta, including on processes built with previous versions of the SDK, and eliminates certain classes of crashes that sometimes required using the legacy API instead. (65051563)

### Localization

#### New Features

- Three Simplified Chinese Wubi input methods are now supported: Wubi 86, Wubi 98, and Wubi New Century. (56277474)

- QuickPath now supports swiping English words on the Simplified Chinese Pinyin keyboard. (56314466)

- Typing numbers using the Japanese Kana keyboard has been significantly enhanced. (56285976)

- CarPlay keyboard support has been added for over 100 additional languages. (56791047)

- Irish Gaelic and Norwegian Nynorsk keyboards now support Auto-Correction. (53156919, 48183197)

### Logging

#### New Features

- New APIs are available for using `os_log` from Swift as part of the framework `os`:

  - A new type, Logger, can be instantiated using a subsystem and category and provides methods for logging at different levels (`Logger.debug`, `Logger.error`, `Logger.fault`).

  - The `Logger` APIs support specifying most formatting and privacy options supported by legacy Logging APIs.

  - The new APIs provide significant performance improvements over the legacy APIs.

  - You can now pass Swift string interpolation to the os_log function.

  **Note:** The new APIs can’t be back deployed; however, the existing `os_log` API remains available for back deployment. (22539144)

### Maps

#### Known Issues

- After updating to iOS & iPadOS 14 beta 2 or later, user data, such as Favorites, Collections, and Recents no longer syncs with devices running earlier versions of iOS & iPadOS. (65005848)

### Networking

#### New Features

- Experimental HTTP/3 support can be enabled in Safari Settings \> Advanced \> Experimental Features, and enabled system-wide in Developer settings. (62969220)

### RealityKit

#### New Features

- To properly render an augmented reality scene with the post-processing effects available in RealityKit, the pipeline now writes depth information when rendering translucent materials. This makes the order that meshes are drawn more impactful for the final image. To properly author content for this pipeline, break up big meshes into smaller parts, especially when the meshes are intertwined. (66535399)

### Siri

#### New Features

You can use doc://com.apple.documentation/documentation/sirikit/inmediausercontext, Core Spotlight, and Intents to improve media interactions and App Selection. For more information, see Improving Siri Media Interactions and App Selection. (67026608)

### Safari and WebKit

#### New Features

- Webpage Translation is now available in the U.S. and Canada. Supported languages include English, Spanish, Simplified Chinese, French, German, Russian, and Brazilian Portuguese. Safari will automatically detect if translation is available based on your Preferred Languages list. (64437861)

### SKAdNetwork

#### Known Issues

- To receive a postback from devices running iOS 14 or later, generate signatures using signature version 2.0 or later. Version 1.0 signatures don’t result in a postback on iOS 14 and later, even if the advertised app is installed and launched. (71474331)

#### Resolved Issues

- The `source-app-id` and `conversion-value` parameter values are now available in the version 2 install validation postback that the device sends to your ad network’s registered postback URL.

### SwiftUI

#### Known Issues

- The KeyboardShortcut modifier and commands(content:) aren’t currently functional. (65704705)

- Rebuilding against the iOS 14 SDK will modify instances of custom(_:size:) to scale with dynamic type. To create a font which doesn’t scale with dynamic type, use custom(_:fixedSize:). (51463566)

- The SignInWithAppleButton view expands to fill its container. (64136568)

  **Workaround:** Apply a frame modifier.

#### New Features

- doc://com.apple.documentation/documentation/swiftui/view/body-body-8kl5o is now implicitly a ViewBuilder and body is now implicitly a SceneBuilder. (63606493)

- Color can be converted to and from CGColor. The ColorPicker can also now be configured with a binding to a `CGColor`. (56939085)

- Introduced ToolbarItemGroup as a convenient way to place multiple items in a specific location of non-customizable toolbars. (64178863)

- ProgressView now supports adding a secondary “current value label” that describes the current progress level of the task. Use the label to describe the overall task, and the ProgressViewStyleConfiguration.CurrentValueLabel to provide more specific details about the progress of the task. (63580200)

- FileDocument and ReferenceFileDocument have updated protocol requirements:

  - Their initializer requirement now has a single FileDocumentReadConfiguration parameter that the `fileWrapper` and `contentType` can be read from.

  - Their `write()` functions that were expected to write to an inout FileWrapper parameter are now `fileWrapper()` functions that return a `FileWrapper` instead.

  - The document-based app templates in Xcode have been updated to reflect this change in API.

  - Source compatibility with the previous requirements will eventually be removed. (65146043)

- KeyboardShortcut and Commands are now available on iOS & iPadOS. (62614998)

- Image is now redacted when the `AnyView.redacted(reason:)` modifier is applied. (65047189)

- InlinePickerStyle is now available and allows a Picker to appear in-line with the rest of the content in its surrounding container. The style will adapt its appearance for different containers and platforms, such as individual menu items in a menu. (59868844)

- MenuPickerStyle is now available and allows a Picker to present its options within a menu. This style will display its options within a submenu when the `Picker` is nested within a Menu, ContextMenu, or CommandMenu. (65515392)

- List may now be used with ScrollViewReader. (35471164)

- Text gains a new initializer accepting a Formatter. (63641785)

- Menu is now supported on iOS & iPadOS and can be used to create a button that shows a menu as its primary action. (59725999)

- A new redaction reason API for applying placeholder Text treatment is now available. (63288447)

- The `ImportFilesAction` and `ExportFilesAction` APIs have been replaced with a collection of new view modifiers.

- Use the new `.fileImporter()` modifier to present a system interface for importing one or more files into your app, and the new `.fileMover()` modifier to move one or more existing files to a new location. The following is an example of a simple UI for importing and moving files:

  ```
  ```

- Use the new `.fileExporter()` modifier to present a system interface for exporting one or more documents from your app. In this example, an app provides a simple note-taking interface for quickly jotting down some text and then exporting it to disk:

  ```
  ```

- Use the new `.fileMover()` modifier to present a system interface for moving one or more existing files to a new location. (66182201)

#### Resolved Issues

- Rebuilding against the iOS 14 SDK will change uses of GeometryReader to reliably top-leading align the views inside the `GeometryReader`. This was the previous behavior, except when it was not possible to detect a single static view inside the `GeometryReader`. (59722992)

### Third-Party Apps

#### Known Issues

- Apps using JSONKit might quit unexpectedly on launch. Some forks of JSONKit hardcode private, pointer-representation details, which are subject to change. (60290929)

  **Workaround:** Use NSJSONSerialization instead.

- `fstab` has been removed. You can no longer use Filesystem contents outside of an app’s sandbox for validation. (61098152)

- Apps using the NativeScript framework might quit unexpectedly on launch. NativeScript performs an unsafe operation to determine if an arbitrary pointer is an Objective-C object pointer. You can temporarily resolve this issue by using doc://com.apple.documentation/documentation/objectivec/1418629-object_getclass instead of reading the `isa` directly; however, update this code to avoid checking whether arbitrary pointers are Objective-C object pointers. (62913064)

### Vision

#### Deprecations

- The `VNIdentifiedPointsObservation` class is deprecated. Use VNRecognizedPointsObservation instances instead. (63690311)

### Voice Control

#### New Features

- Voice Control is now available in English (United Kingdom) and English (India). (55904557)

### Wallet

#### Known Issues

- isPassLibraryAvailable() doesn’t ensure uniform availability of pass library functionality between platforms and devices. (60697880)

  **Workaround:** Call a more specific API to check available functionality, such as canAddPasses().

#### New Features

- Apple Pay support is now available to Mac Catalyst apps. Two methods have been added to existing delegate protocols. No changes are required for iPad apps, but one or both of these methods must be implemented when building for Catalyst. (64187739)

  - The first method is an addition to the PKPaymentAuthorizationControllerDelegate protocol: presentationWindow(for:). This method is required for Catalyst when using PKPaymentAuthorizationController, because `PKPaymentAuthorizationController`, unlike PKPaymentAuthorizationViewController, doesn’t have knowledge of the window requesting presentation of the payment sheet. Pass back the `UIWindow` instance displaying the UI requesting the payment, for example, `MyViewController.view.window`. This method is marked as required when building for Catalyst, but is otherwise optional.

  - The second method depends on whether you’re using `PKPaymentAuthorizationController` or `PKPaymentAuthorizationViewController`. For `PKPaymentAuthorizationControllerDelegate`, use paymentAuthorizationController(_:didRequestMerchantSessionUpdate:). For `PKPaymentAuthorizationViewControllerDelegate`, use paymentAuthorizationViewController(_:didRequestMerchantSessionUpdate:).

- This method must be implemented to request a merchant session via your server, and return it via the handler. This mirrors the security model used in WebKit, and replaces listing merchant IDs in the app’s Apple Pay entitlements. This method in turn uses the following class to send back results:

  ```
  API_AVAILABLE(macos(10.16), ios(14.0), watchos(7.0))
  @interface PKPaymentRequestMerchantSessionUpdate : NSObject

  - (instancetype)initWithStatus:(PKPaymentAuthorizationStatus)status
                 merchantSession:(nullable PKPaymentMerchantSession *)session;

  @property (nonatomic, assign) PKPaymentAuthorizationStatus status;
  @property (nullable, nonatomic, strong) PKPaymentMerchantSession *session;

  @end
  ```

### Weather

#### New Features

- Government alerts about certain severe weather events including tornados, winter storms, flash floods, and more are now available in the U.S., Europe, Japan, Canada, and Australia. (58931042)

### Widgets

#### Known Issues

- When the parent app of a widget has been granted Selected Photos access, an alert might appear each time the widget runs. (66398732)

  **Workaround:** Add `PHPhotoLibraryPreventAutomaticLimitedAccessAlert = YES` to the Info.plist of the widget extension.

- All widgets must be rebuilt using the iOS & iPadOS 14 beta 4 SDK or later, and won’t run on previous versions of iOS & iPadOS 14 beta. (65290210)

- Some widgets might disappear from your Home Screen after updating to iOS & iPadOS 14 beta 2 or later. (64823469)

  **Workaround:** Add the missing widgets back to your Home Screen.

- You can’t resize an existing widget. (63500799)

  **Workaround:** Remove the widget and re-add it at the desired size.

- You might need to reconfigure your widgets after updating to iOS & iPadOS 14 Beta 3 or later. (65485709)

- The Weather widget might appear blank after updating to iOS 14 beta 6 or later. (66782070)

  **Workaround:** Tap the widget to open the Weather app, then return to the widget on the Home screen.

## See Also

### iOS &amp; iPadOS 14

iOS & iPadOS 14.7 Release Notes

Update your apps to use new features, and test your apps against API changes.

iOS & iPadOS 14.6 Release Notes

Update your apps to use new features, and test your apps against API changes.

iOS & iPadOS 14.5.1 Release Notes

Update your apps to use new features, and test your apps against API changes.

iOS & iPadOS 14.5 Release Notes

Update your apps to use new features, and test your apps against API changes.

iOS & iPadOS 14.4 Release Notes

Update your apps to use new features, and test your apps against API changes.

iOS & iPadOS 14.3 Release Notes

Update your apps to use new features, and test your apps against API changes.

iOS & iPadOS 14.2 Release Notes

Update your apps to use new features, and test your apps against API changes.

