

- iOS &amp; iPadOS Release Notes
-  iOS & iPadOS 15 Release Notes 

Article

# iOS & iPadOS 15 Release Notes

Update your apps to use new features, and test your apps against API changes.

## Overview

The iOS & iPadOS 15 SDK provides support to develop apps for iPhone, iPad, and iPod touch devices running iOS & iPadOS 15. The SDK comes bundled with Xcode 13, available from the Mac App Store. For information on the compatibility requirements for Xcode 13, see Xcode 13 Release Notes.

### App Store

#### New Features

- StoreKit 2 introduces a modern Swift-based API that takes advantage of new language features like Swift concurrency. Use this API to load product information, display in-app purchases in your store, allow customers to make purchases, manage access to content and subscriptions, and receive transaction information signed by the App Store in JSON Web Signature (JWS) format. (66587964)

- The `request(with:)` type method on Product is now renamed to products(for:). (79410910)

- The Transaction `listener` type properties on Product.SubscriptionInfo.Status and Storefront are now updates and updates, respectively. The nested AsyncSequence conforming structures are now Transaction.Transactions, Product.SubscriptionInfo.Status.Statuses, and Storefront.Storefronts. Both `TransactionSequence` and `TransactionListener` are now Transaction.Transactions. (79034347)

- `StoreKitError.userDidNotAuthenticate` is no longer available; use StoreKitError.userCancelled instead. (78270199)

- You can now access Product raw JSON data for custom decoding:

  - Multiple Product.PurchaseOption methods are now allowed. `.custom(_:)` is replaced with several new type methods, namely custom(key:value:), custom(key:value:), custom(key:value:), and custom(key:value:).

  - Subscript operators on Product, Transaction, and renewalInfo are removed, along with the nested `Key` enumerations.

  - `BackingValue` and extensions adding initializers from `BackingValue` are removed. (79101606)

- A new type property unfinished is now available on Transaction that returns signed information for any transactions where the app still needs to deliver content to the user. (79620896)

- A new onStorefrontChange(shouldContinuePurchase:) is available in StoreKit 2. You can use this purchase option to determine whether the transaction continues if the App Store storefront changes during a transaction. The default is `true` if this option isn’t added. (70757789)

- `VerificationResult.unverified(SignedType)` is now `VerificationResult.unverified(SignedType, VerificationError)` to provide a reason for unverified signed values. jsonRepresentation is available on Transaction and jsonRepresentation is available on renewalInfo; both properties provide the payload JSON as `Data`. payloadValue and unsafePayloadValue properties are available on VerificationResult as a convenience to access the signed value. (80701792)

#### Resolved Issues

- Fixed an issue where purchases performed in the Sandbox environment returned `VerificationResult.unverified(_:_:)`. (71949674)

#### Known Issues

- The unfinished property might return `VerificationResult` for transactions that have already finished. (81346114)

### Audio Units

#### New Features

- Audio Units now provides custom views that Audio Unit hosts can display in iOS. Use the providesUserInterface property to determine if an AUAudioUnit has a user interface. Use the requestViewController(completionHandler:) method to get the AUViewController for the view. The custom view supports setting the tint color of the view via the tintColor property. This can be used to set the color of the view to a different color for each track or to match the look of the app. (74183251)

### AVFoundation

#### New Features

- iPadOS apps can now continue using the camera while presenting multiple windows and being the only application onscreen. (77522226)

#### Deprecations

- supportedPhotoPixelFormatTypes(for:) and supportedRawPhotoPixelFormatTypes(for:) now return `[OSType]` instead of `[NSNumber]` in Swift. (64822071)

- recommendedVideoSettings(forVideoCodecType:assetWriterOutputFileType:) now returns `nullable NSDictionary *` instead of `nullable NSDictionary *` in Objective-C and `[String: Any]?` instead of `[AnyHashable: Any]?` in Swift. (33784279)

- cgImageRepresentation() and previewCGImageRepresentation() now return `CGImage?` instead of `Unmanaged?` in Swift. (44734827)

- recommendedAudioSettingsForAssetWriter(writingTo:) now returns `nullable NSDictionary *` instead of `nullable NSDictionary *` in Objective-C and `[String: Any]?` instead of `[AnyHashable: Any]?` in Swift. (50450334)

### Core Haptics

#### New Features

- Events of type audioContinuous, hapticContinuous, and audioCustom now resume playback mid-event if a paused CHHapticAdvancedPatternPlayer resumes. These events don’t begin mid-event if seek(toOffset:) starts the player at a specific time offset. (29274583)

- You can now control whether to apply a volume envelope to type resources. By default, these resources play back with a built-in volume envelope that ramps the signal in at the beginning and ramps out at the end, to avoid clicks. (75491090)

  You can apply a volume envelope in one of the following ways:

  - If you’re importing custom audio assets by registering audio resource IDs for them, you can specify this behavior via a new key value argument, CHHapticAudioResourceKeyUseVolumeEnvelope, that the system passes to registerAudioResource(_:options:).

  - If you’re referencing audio assets using an AHAP file or the init(dictionary:) of CHHapticPattern, you can control this behavior with the `CHHapticPatternKeyEventWaveformUseVolumeEnvelope` pattern key.

### Core ML

#### Known Issues

- In automatic reference counting (ARC) mode, the compiler may extend the lifetime of `MLMultiArray` longer than expected when the `.dataPointer` property is used. This may increase memory usage. (80895213)

  **Workaround:** Enclose `.dataPointer` access in an `@autoreleasepool {... }` block.

### Create ML

#### New Features

- The Create ML framework is now available in iOS & iPadOS 15, unlocking new opportunities for building dynamic app experiences that leverage on-device ML. Task-focused APIs for image classification, sound classification, text classification, and hand pose and hand action classification are available, along with APIs for classical tabular classification and regression. (37087332)

- The Audio Feature Print-based MLSoundClassifier algorithm trains sound classifier models faster, with higher accuracy, lower latency, and a smaller model size. This algorithm is now the default option for the `MLSoundClassifier` in Create ML. (70106630)

### Debugging

#### Known Issues

- Using dispatch semaphores in an iOS app running in a device simulator on a Mac with Apple silicon running macOS 11 causes the app to crash. (81783378)

  **Workaround:** In Xcode, select Product \> Scheme \> Edit Scheme, then deselect Run \> Options \> Queue Debugging \> “Enable backtrace recording.”

### Find My

#### Known Issues

- When your iOS device needs to be charged, text indicating that the Find My network is active only displays if the device language is set to English. (78547946)

### Guided Access

#### Known Issues

- When using Guided Access with VoiceOver, you might be unable to enter the Guided Access passcode to end Guided Access. (79370792)

  **Workaround:** If a device passcode is set, force restart your device to end Guided Access.

### Home

#### Known Issues

- You can’t pair with Matter accessories that use Thread. (80991829)

- You can’t pair a third-party app with Matter accessories through the app paring flow if the accessory is already paired with another app. (80059432)

  **Workaround:** Remove accessory pairing from other apps, then pair the third-party app.

- You can’t add a flow to a third-party app with Matter accessories if you haven’t created an Apple Home. (80058744)

  **Workaround:** Launch the Home app to create a Home before you add a flow.

- Matter accessories aren’t reachable while Apple TV is connected via Wi-Fi. (79582629)

  **Workaround:** Connect Apple TV via Ethernet.

- Matter accessories might enter a No Response state after pairing. (76019163)

  **Workaround:** Remove the accessory from Home, reset the accessory, and add it back to Home. If the issue persists, remove your Home hub from Home and re-add it. If the issue still persists, remove the home and create a new one.

- The initial pairing attempt with a Matter accessory might take an unexpectedly long time and eventually fail. (77967587)

  **Workaround:** Retry pairing the accessory.

- You can only pair up to five Matter accessories in a home. (77967671)

- Only the owner of a home, not an invited user, can pair Matter accessories. (76012945)

### Home Screen

#### Known Issues

- After canceling a search in the widget gallery, the cancel button remains visible, which might blank out the widget gallery. (78572049)

  **Workaround:** Dismiss and reopen the widget gallery.

### iCloud

#### New Features

- iCloud Private Relay will be released as a public beta to gather additional feedback and improve website compatibility. (82150385)

#### Known Issues

- Legacy Contacts has been removed from iOS & iPadOS 15 beta 5 and will return in a future release. (81292885)

- Custom Email Domain addresses with delimiters like “+” or “-” can’t be configured. (82425376)

- Custom Email Domain addresses that are associated with a separate iTunes account can’t be configured. (82358431)

- Some accounts may not yet be eligible for Custom Email Domain. (82421769)

### Foundation

#### New Features

- Foundation now includes an automatic grammar agreement engine. This simplifies your code and reduces the number of localized strings you provide by automatically inflecting localized strings to account for pluralization, grammatical gender agreement, and agreement with the user’s term of address. It’s available for English and Spanish. (70210115)

- Formatting APIs are now available, which focus on the format and remove the need to create, configure, and cache a formatter instance. Each Formatter type has a `formatted` function. These functions have arguments that allow for configuration and customization of the style. (70220307)

- JSONSerialization and JSONDecoder now support decoding from JSON5. (73954652)

- SortDescriptor, KeyPathComparator, and SortComparator APIs provide a Swift interface to express archivable rules for sorting values. (74264359)

### Logging

#### New Features

- os_signpost(_:dso:log:name:signpostID:) from Swift is part of the framework OS on all platforms:

  - Instantiate OSSignposter using a subsystem and category, an existing OSLog object, or an existing Logger object.

  - The OSSignposter API provides methods for emitting signposts. beginInterval(_:id:) emits `begin` signposts, endInterval(_:_:) emits `end` signposts, and emitEvent(_:id:) emits `event` signposts. These replace the existing `os_signpost` calls based on `String` and `varargs`.

  - The APIs support `String` interpolations for the metadata parameter. The `String` interpolations are the same as those accepted by the Logger APIs.

  - The OSSignposter API supports all formatting and privacy options — previously offered by the `os_signpost` functions — and follows the same syntax as the Logger APIs.

  - The APIs provide performance improvements over the legacy APIs.

  - The `OSSignposter type` provides a new scoped API for surrounding a block of code by `begin` and `end` signposts, withIntervalSignpost(_:id:_:around:).

  **Note:** These APIs are unavailable in iOS 14 and iPadOS 14 and earlier; however, the existing `os_signpost` API remains available. (54756831)

### Maps

#### Known Issues

- Rounded building corners might disappear. (80468151)

#### Deprecations

- MKPinAnnotationView and MapPin are marked as deprecated in this beta. (78536295)

### Networking

#### New Features

- The default `Accept-Language` header that URLSession sends has an updated format and corrected values for multiple locales. In addition to the preferred language, the header also includes the current system language as a fallback if it differs from the preferred language. This behavior affects apps that link against macOS 12, iOS 15, tvOS 15, and watchOS 8 SDKs. (38772422)

- `URLSession` now includes `async` functions. (68890254)

  For example, a one-shot fetch:

  ```
  let (data, response) = try await URLSession.shared.data(from: URL(string: "https://www.apple.com")!)
  if let httpResponse = response as? HTTPURLResponse, httpResponse.statusCode == 200 {
     // Use data.
  }
  ```

  And support for an AsyncSequence stream of bytes:

  ```
  let (bytes, response) = try await URLSession.shared.bytes(with: URL(string: "https://www.apple.com")!)
  if let httpResponse = response as? HTTPURLResponse, httpResponse.statusCode == 200 {
      for try await line in bytes.lines() {
          // Parse line.
      }
  }
  ```

#### Deprecations

- Support for cleartext HTTP URL schemes for Proxy Automatic Configuration (PAC) is now deprecated. Use only HTTPS URL schemes for PAC. This affects all PAC configurations, including, but not limited to, configurations set via Settings, System Preferences, profiles, and `URLSession` APIs such as connectionProxyDictionary and CFNetworkExecuteProxyAutoConfigurationURL(_:_:_:_:). If you configure a cleartext HTTP PAC URL, the system may upgrade it to HTTPS during PAC file loads. Web Proxy Auto-Discovery (WPAD) Protocol via DNS isn’t affected. Dynamic Host Configuration Protocol (DHCP) Option 252 WPAD may attempt to upgrade cleartext HTTP URLs to HTTPS during PAC file loads. (61981845)

### Privacy

#### New Features

- To download a file that shows the app content in the App Privacy Report, choose Settings \> Privacy \> Record App Activity. (77758720)

### Reality Composer

#### Known Issues

- You might be unable to create new projects in Reality Composer. (79418400)

  **Workaround:** Create a new project in Reality Composer on macOS and transfer the `.rcproject` file to your device via AirDrop or Mail.

### Safari

#### New Features

- The bottom tab bar is redesigned to appear below page content. An option to show the address bar at the top is also available. (81118141)

#### Known Issues

- When tapping in an input field in a Safari Web Extension popover on iPhone, the Extension UI might not move upward to make room for the keyboard. (81676564)

### SharePlay

#### Deprecations

- SharePlay development in beta 7 and upcoming beta releases requires the installation of an updated SharePlay Development Profile. This profile enables successful creation and reception of GroupSessions via the Group Activities API in iOS 15, iPadOS 15 and tvOS 15 beta 7, as well as macOS Monterey beta 6. (81816137)

### ShazamKit

#### Known Issues

- Media items added to the default instance of SHMediaLibrary don’t appear in Shazam. (77785557)

  **Workaround:** Touch and hold the Music Recognition Control Center module to view SHMediaLibrary contents.

### Siri

#### Known Issues

- VoiceOver and Spoken Content users might not initially see all available voice options. Voice options should populate after some time. (79463000)

- On-device speech recognition only supports the following languages: Chinese (Mandarin - China mainland), English (Australia), English (Canada), English (United Kingdom), and English (US). (78483609)

### SKAdNetwork

#### New Features

- If a developer opts-in to receive the winning postback, devices can now send a copy of the winning postback to the advertised app’s developer. (75054513)

### Swift

#### New Features

- A new Swift value type AttributedString is now available with the same character-counting behavior as a Swift string. It’s fully localizable, and also includes support for Markdown, Codable, strongly typed attributes, and more. (27227292)

- NotificationCenter includes a new AsyncSequence API for receiving notifications using async/await. (74401384)

  ```
  for await note in NotificationCenter.default.notifications(named: .MyNote) {
      // Use note.
  }
  ```

#### Known Issues

- Swift libraries depending on Combine may fail to build for targets including ARMv7 and i386 architectures. (82183186, 82189214)

  **Workaround:** Use an updated version of the library that isn’t impacted (if available) or remove ARMv7 and i386 support (for example, increase the deployment target of the library to iOS 11 or higher).

- Applications linking to RealityKit with the iOS 15 or macOS 12 SDKs will fail to launch on a previous OS. (79584511)

  **Workaround:** Add `OTHER_LD_FLAGS = -weak_framework RealityFoundation` to your Xcode Project settings to allow running RealityKit apps on an older OS.

### Settings

#### Known Issues

- While the Sound Actions feature work as part of Switch Control, sounds aren’t detected in the area marked Practice in Settings app. (82411537)

### SwiftUI

#### New Features

- LocalizedStringKey can now contain Markdown syntax. The system parses Markdown strings when you create a Text view from a `LocalizedStringKey`, including `Text` views created with a string literal. The system styles `Text` according to Markdown constructs. (74515884)

- You can create Text from an AttributedString structure. `Text` respects the styles you provide through attributes within the SwiftUI attribute scope; these styles take precedence over styles you provide through view modifiers. (74841755)

- Specific kinds of animations now execute off the main thread, so there are new thread-safety requirements. (70524799)

  Ensure the following functions and types are thread-safe:

  - All methods and accessors of types conforming to the protocols AlignmentID, Animatable, EnvironmentKey, EnvironmentValues, Equatable, GeometryEffect, Hashable, Identifiable, PreferenceKey, Shape, VectorArithmetic.

  - Any closures you pass to the following types and functions, but only if the views that created them don’t have references to ObservableObject types: ForEach, GeometryReader, doc://com.apple.documentation/documentation/swiftui/hstack/backgroundpreferencevalue(\_:\_:), doc://com.apple.documentation/documentation/swiftui/emptyview/overlaypreferencevalue(\_:\_:), doc://com.apple.documentation/documentation/swiftui/hstack/transformpreference(\_:\_:), doc://com.apple.documentation/documentation/swiftui/hstack/anchorpreference(key:value:transform:), doc://com.apple.documentation/documentation/swiftui/hstack/transformanchorpreference(key:value:transform:), doc://com.apple.documentation/documentation/swiftui/hstack/transformenvironment(\_:transform:), doc://com.apple.documentation/documentation/swiftui/form/transaction(\_:).

- A TextField provided an NSFormatter now updates its binding as the user types. `NSFormatter` formats the text of the field when the user submits the field, or when focus moves away from the field. (67899823)

- A DisclosureGroup now toggles its expansion when tapping the row. (62208702)

- The default ListStyle is now insetGrouped. (75072988)

- TextField labels don’t appear next to the field in a form. Use the `prompt` parameter to specify an explicit placeholder for the field. (61260160)

- You can now initialize Text with a FormatStyle. (72159423)

- While searching, if you tap a suggestion that uses the doc://com.apple.documentation/documentation/swiftui/anyview/searchcompletion(\_:) modifier, the suggestion list now disappears rather than displaying the single suggestion you selected. (76965399)

- You can now customize the prompt of a search field that a searchable modifier configures using the `prompt` parameter instead of the previous `title` parameter. (77988967)

- SwiftUI now supports `textSelection` modifiers. (77827592)

- Added `buttonBorderShape`, which can be used to control the shape of bordered buttons. (79456465)

- Added new AttributedString attributes underlineStyle and strikethroughStyle to AttributeScopes.SwiftUIAttributes. (78437803)

- Types conforming to the Animatable protocol and also conforming to either the View or ViewModifier protocols now apply animations when their values change. Consequently, the AnimatableModifier protocol is soft-deprecated. Use `Animatable` directly when targeting the latest OS versions; for example, use `struct CustomModifier: ViewModifer, Animatable` rather than `struct CustomModifier: AnimatableModifier`. (76971100)

- The contentShape(_:eoFill:) modifier now allows fine-grained control over different kinds of shapes. For drag previews, hover effects, and context menus, the matching `ContentShapeKinds` is required to affect the shape of previews when linked on iOS 15.0 or newer. The default behavior is to set the `interaction` kind. (60792377)

- The openURL environment value can now be set and used to customize URL handling in the view hierarchy, including URL handling in Link views and links embedded in Text views. (78551237)

- Task allows you to pass the priority to be used when spawning a new `Task`. (80599258)

- Text views that contain excessive line height characters now have a larger default size to avoid clipping or overlapping of oversized characters. (80665315)

- A NavigationLink in a sidebar on iPad that uses `isDetailLink(false)` correctly pushes onto the sidebar rather than the detail area. (80919171)

#### Known Issues

- Providing a binding to an OutlineGroup might require including wrappedValue in the init(_:children:content:) key path parameter, and isn’t available in iOS & iPadOS 14 and earlier. (77890799)

- Focusing a view in a newly added List row using FocusState requires deferring the focus state property update to the next time the main runloop runs. (78607356)

- List no longer respects SwiftUI’s safe area insets. (82295913)

#### Deprecations

- `controlProminence` is deprecated. Use the new `.borderedProminent` ButtonStyle instead. (78908460)

- The Function (`Fn`) shortcut modifier is deprecated and reserved for system usage. (78627099)

### TabularData

#### New Features

- TabularData is a new Swift framework you use to analyze and manipulate tabular data. You can use DataFrame to read CSV and JSON files, as well as join, group, and aggregate data. (69982458)

### UIKit

#### New Features

- For apps compiled against the iOS 15 beta SDK, key commands no longer intercept text input and text editing commands while typing into text views and text fields. For example, pressing the Delete key always deletes a character and doesn’t trigger a Delete key command if one is present. To have a key command intercept text input, set the wantsPriorityOverSystemBehavior property to `true` on the key command. This is also required to have key commands take priority over focus keyboard navigation commands, such as arrow and tab key presses. (55118263)

- In iOS 14 and iPadOS 14 and earlier, when autocorrectionType is set to UITextAutocorrectionType.no, the QuickType bar is disabled. For apps linked against iOS 15 and iPadOS 15 or later, the QuickType bar is enabled and shows spellchecking candidates. If the new behavior isn’t desirable for your use case, set spellCheckingType to UITextSpellCheckingType.no to hide the QuickType bar. (68874861)

- When compiling with the iOS 15 beta SDK, several key window-related properties, methods, and notifications change behavior:

  - isKeyWindow returns `true` if the window is key in its scene instead of the app.

  - becomeKey() is called when the window becomes key in its scene instead of the app.

  - didBecomeKeyNotification posts when the window becomes key in its scene instead of the app.

  - resignKey() is called when the window resigns key window status in its scene instead of the app.

  - didResignKeyNotification posts when the window resigns key window status in its scene instead of the app. (72873846)

### Xcode

#### Known Issues

- MusicKit functionality, such as loading content with music requests, doesn’t work in simulated devices. (78559381)

## See Also

### iOS &amp; iPadOS 15

iOS & iPadOS 15.6 Release Notes

Update your apps to use new features, and test your apps against API changes.

iOS & iPadOS 15.5 Release Notes

Update your apps to use new features, and test your apps against API changes.

iOS & iPadOS 15.4 Release Notes

Update your apps to use new features, and test your apps against API changes.

iOS & iPadOS 15.3 Release Notes

Update your apps to use new features, and test your apps against API changes.

iOS & iPadOS 15.2 Release Notes

Update your apps to use new features, and test your apps against API changes.

iOS & iPadOS 15.1 Release Notes

Update your apps to use new features, and test your apps against API changes.

