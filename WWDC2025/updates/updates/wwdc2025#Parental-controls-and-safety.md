![An icon, with three sparkle images, representing what's new.](https://docs-assets.developer.apple.com/published/4d8fd4841fb4f273ebbd5a3a0648878e/new.svg)

*   [Updates](/documentation/updates)
*   WWDC25

# WWDC25

Highlights of new technologies introduced at WWDC25.

## [Overview](/documentation/updates/wwdc2025#Overview)

Browse a selection of documentation for new technologies and frameworks introduced at WWDC25. Many existing frameworks have added significant functionality to enhance your apps when run on the latest platform releases.

For a comprehensive list of downloadable sample code projects, see [WWDC25 Sample Code](https://developer.apple.com/documentation/samplecode/). To tour the frameworks and tools for Apple platforms, browse [Technology Overviews](/documentation/TechnologyOverviews). For the latest design guidance, see [Human Interface Guidelines > What’s New](https://developer.apple.com/design/whats-new/).

## [Topics](/documentation/updates/wwdc2025#topics)

### [Accessibility](/documentation/updates/wwdc2025#Accessibility)

Add Accessibility Nutrition Labels to your App Store product page to highlight features you support to give your app a greater reach. For instance, a person that requires reading glasses may search the store for apps that support Larger Text.

[

Accessibility](/documentation/Accessibility)

Make your apps accessible to everyone who uses Apple devices.

### [App services](/documentation/updates/wwdc2025#App-services)

[

PaperKit](/documentation/PaperKit)

Add drawings, shapes, and a consistent markup experience to your app.

[

EnergyKit](/documentation/EnergyKit)

Provide a grid forecast for your app to help people choose when to use electricity.

Beta

[

Performing long-running tasks on iOS and iPadOS](/documentation/BackgroundTasks/performing-long-running-tasks-on-ios-and-ipados)

Use a continuous background task to do work that can complete as needed.

[`final actor SpeechAnalyzer`](/documentation/Speech/SpeechAnalyzer)

Analyzes spoken audio content in various ways and manages the analysis session.

Beta

[

Creating custom views for Live Activities](/documentation/ActivityKit/creating-custom-views-for-live-activities)

Create reusable custom views and layouts that support each Live Activity presentation.

[

Launching your app from a Live Activity](/documentation/ActivityKit/launching-your-app-from-a-live-activity)

Use deep links to enable people to open your app’s scene that matches the data of you Live Activity.

[

Configuring App Clip experiences](/documentation/AppClip/configuring-the-launch-experience-of-your-app-clip)

Review how people launch your App Clip with invocation URLs, default and demo links, and advanced App Clip experiences.

### [App Store distribution and marketing](/documentation/updates/wwdc2025#App-Store-distribution-and-marketing)

[

Understanding StoreKit workflows](/documentation/StoreKit/understanding-storekit-workflows)

Implement an in-app store with several product types, using StoreKit views.

Beta

[

Configuring your Background Assets project](/documentation/BackgroundAssets/configuring-background-assets)

Edit your app and extension targets in your Xcode project to use Background Assets.

[

Background Assets](/documentation/BackgroundAssets)

Schedule background downloads of large assets during or after app installation, when the app updates, and periodically while the app remains on-device.

[

Configuring attribution rules for your app](/documentation/AdAttributionKit/configuring-attribution-rules-for-your-app)

Tune aspects of attribution flow, including the time available to register impressions and the minimum time your app is willing to accept conversions.

[

Identifying the parameters in a postback](/documentation/AdAttributionKit/identifying-the-parameters-in-a-postback)

Interpret postback properties to understand the attribution report.

[

Receiving postbacks in multiple conversion windows](/documentation/AdAttributionKit/receiving-postbacks-in-multiple-conversion-windows)

Learn about the data that postbacks can contain in each conversion window.

[

Packaging and distributing Safari Web Extensions with App Store Connect](/documentation/SafariServices/packaging-and-distributing-safari-web-extensions-with-app-store-connect)

Upload and distribute Safari Web Extensions without using a Mac or Xcode.

### [Apple Intelligence and machine learning](/documentation/updates/wwdc2025#Apple-Intelligence-and-machine-learning)

[

Apple Intelligence and machine learning](/documentation/TechnologyOverviews/ai-machine-learning)

Add intelligent features with Apple Intelligence, machine learning, and related technologies.

[

Foundation Models](/documentation/FoundationModels)

Perform tasks with the on-device model that specializes in language understanding, structured output, and tool calling.

Beta

[

Improving safety from generative model output](/documentation/FoundationModels/improving-safety-from-generative-model-output)

Create generative experiences that appropriately handle sensitive inputs and respect people.

[

Integrating actions with Siri and Apple Intelligence](/documentation/AppIntents/Integrating-actions-with-siri-and-apple-intelligence)

Create app intents, entities, and enumerations that conform to assistant schemas to tap into the enhanced action capabilities of Siri and Apple Intelligence.

[

Displaying static and interactive snippets](/documentation/AppIntents/displaying-static-and-interactive-snippets)

Enable people to view the outcome of an app intent and immediately perform follow-up actions.

[

Making app entities available in Spotlight](/documentation/AppIntents/making-app-entities-available-in-spotlight)

Allow people to find your app’s content in Spotlight by donating app entities to its semantic index.

[

Generating content and performing tasks with Foundation Models](/documentation/FoundationModels/generating-content-and-performing-tasks-with-foundation-models)

Enhance the experience in your app by prompting an on-device large language model.

[

Visual Intelligence](/documentation/VisualIntelligence)

Include your app’s content in search results that visual intelligence provides.

Beta

[

Integrating your app with visual intelligence](/documentation/VisualIntelligence/integrating-your-app-with-visual-intelligence)

Enable people to find app content that matches their surroundings or objects onscreen with visual intelligence.

[

Recognizing tables within a document](/documentation/Vision/recognize-tables-within-a-document)

Scan a document containing a contact table and extract the content within the table in a formatted way.

Beta

```swift
```swift
```swift
struct DetectLensSmudgeRequest
```
```

A request that detects a smudge on a lens from an image or video frame capture.

Beta
```

### [Apple Pay and Wallet](/documentation/updates/wwdc2025#Apple-Pay-and-Wallet)

[

Implementing as an identity document provider](/documentation/IdentityDocumentServices/Implenting-as-an-identity-document-provider)

Add your app as an option for mobile document web presentment.

[

IdentityDocumentServices](/documentation/IdentityDocumentServices)

Share mobile documents using the Digital Credentials API.

Beta

[

IdentityDocumentServicesUI](/documentation/IdentityDocumentServicesUI)

Provide an interface so people can present mobile documents.

Beta

[

Setting up Tap to Pay on iPhone](/documentation/ProximityReader/setting-up-the-entitlement-for-tap-to-pay-on-iPhone)

Request and configure the required entitlement to support Tap to Pay on iPhone.

### [Audio, Video, and Media](/documentation/updates/wwdc2025#Audio-Video-and-Media)

[

Signing people in to their media accounts automatically](/documentation/VideoSubscriberAccount/signing-people-in-to-media-apps-automatically)

Implement single sign-on for media-streaming apps by managing a sign-in token on a person’s Apple Account.

[

Video Subscriber Account](/documentation/VideoSubscriberAccount)

Support TV provider and Apple TV app functionality.

[

Automatic Sign-In API](/documentation/AutomaticSignInAPI)

Manage sign-in tokens that facilitate single sign-on across the devices of your media streaming service customers from your web server.

[

Capturing Spatial Audio in your iOS app](/documentation/AVFoundation/capturing-spatial-audio-in-your-ios-app)

Enhance your app’s audio recording capabilities by supporting Spatial Audio capture.

Beta

[

Editing Spatial Audio with an audio mix](/documentation/Cinematic/editing-spatial-audio-with-an-audio-mix)

Add Spatial Audio editing capabilities with the Audio Mix API in the Cinematic framework.

Beta

[

Enhancing your app with machine learning-based video effects](/documentation/VideoToolbox/enhancing-your-app-with-machine-learning-based-video-effects)

Add powerful effects to your videos using the VideoToolbox VTFrameProcessor API.

[

Observing playback state in SwiftUI](/documentation/AVFoundation/observing-playback-state-in-swiftui)

Keep your user interface in sync with state changes from playback objects.

[

Anchoring sound to a window or volume](/documentation/AudioToolbox/spatializing-sound-from-a-uiscene)

Provide unique app experiences by attaching sounds to windows and volumes in 3D space.

[

Creating a seamless multiview playback experience](/documentation/AVFoundation/creating-a-seamless-multiview-playback-experience)

Build advanced multiview playback experiences with the AVFoundation and AVRouting frameworks.

Beta

### [Developer tools](/documentation/updates/wwdc2025#Developer-tools)

[

Creating your app icon using Icon Composer](/documentation/Xcode/creating-your-app-icon-using-icon-composer)

Use Icon Composer to stylize your app icon for different platforms and appearances.

[

Writing code with intelligence in Xcode](/documentation/Xcode/writing-code-with-intelligence-in-xcode)

Generate code, fix bugs fast, and learn as you go with intelligence built directly into Xcode.

[

Running code snippets using the playground macro](/documentation/Xcode/running-code-snippets-using-the-playground-macro)

Add playgrounds to your code that run and display results in the canvas.

[

Understanding and improving SwiftUI performance](/documentation/Xcode/understanding-and-improving-swiftui-performance)

Identify and address long-running view updates, and reduce the frequency of updates.

[

Analyzing the performance of your shipping app](/documentation/Xcode/analyzing-the-performance-of-your-shipping-app)

View power and performance metrics for apps you distribute through the App Store.

[

Recording UI automation for testing](/documentation/XCUIAutomation/recording-ui-automation-for-testing)

Capture and replay interaction sequences to verify your app’s behavior.

[

Downloading and installing additional Xcode components](/documentation/Xcode/downloading-and-installing-additional-xcode-components)

Add more Simulator runtimes, optional features, and support for additional platforms.

[

Measuring your app’s power use with Power Profiler](/documentation/Xcode/measuring-your-app-s-power-use-with-power-profiler)

Profile your app’s power impact whether or not your device is connected to Xcode.

### [Graphics and games](/documentation/updates/wwdc2025#Graphics-and-games)

[

Game technologies](/documentation/TechnologyOverviews/games-technologies)

Plan the creation of your game and incorporate the gameplay features people expect.

[

GameSave](/documentation/GameSave)

Store and sync your application’s save files in iCloud.

Beta

[

Touch Controls](/documentation/TouchControls)

Integrate on-screen touch controls into your Metal-based games.

Beta

[

Discovering and tracking spatial game controllers and styli](/documentation/GameController/discovering-and-tracking-spatial-game-controllers-and-styli)

Receive controller and stylus input to interact with content in your augmented reality app.

[

Creating activities for your game](/documentation/GameKit/creating-activities-for-your-game)

Use activities to surface game content to players and encourage them to connect with each other.

```swift
```swift
```swift
class GKGameActivity
```
```

An object that represents a single instance of a game activity for the current game.

Beta
```

[

Choosing a leaderboard for your challenges](/documentation/GameKit/choosing-a-leaderboard-for-your-challenges)

Understand what gameplay works well when configuring challenges in your game.

[

Creating engaging challenges from leaderboards](/documentation/GameKit/creating-engaging-challenges-from-leaderboards)

Encourage friendly competition by adding challenges to your game.

[

Building your macOS game remotely from your PC](/documentation/TechnologyOverviews/building-your-macos-game-remotely-from-your-pc)

Configure a Mac for remote builds, and use it to build your game from your PC and catch mistakes when porting your game to macOS.

### [Maps and location](/documentation/updates/wwdc2025#Maps-and-location)

[

GeoToolbox](/documentation/GeoToolbox)

Determine place descriptor information for map coordinates.

Beta

```swift
```swift
```swift
struct PlaceDescriptor
```
```

A structure that contains identifying information about a place that a mapping service may use to attempt to find rich place information such as phone numbers, websites, and so on.

Beta
```

[`interface mapkit.LookAround`](/documentation/MapKitJS/mapkit.LookAround)

A view that allows someone to see a street level view of a place.

[`interface mapkit.LookAroundPreview`](/documentation/MapKitJS/mapkit.LookAroundPreview)

A class that renders a preview of a LookAround view.

### [Metal](/documentation/updates/wwdc2025#Metal)

[

Understanding the Metal 4 core API](/documentation/Metal/understanding-the-metal-4-core-api)

Discover the features and functionality in the Metal 4 foundational APIs.

[

Using the Metal 4 compilation API](/documentation/Metal/using-the-metal-4-compilation-api)

Control when and how you compile an app’s shaders.

[

Using a Render Pipeline to Render Primitives](/documentation/Metal/using-a-render-pipeline-to-render-primitives)

Render a colorful, 2D triangle by running a draw command on the GPU.

[

Processing a texture in a compute function](/documentation/Metal/processing-a-texture-in-a-compute-function)

Create textures by running copy and dispatch commands in a compute pass on a GPU.

Beta

[

Machine-Learning Passes](/documentation/Metal/machine-learning-passes)

Add machine-learning model inference to your Metal app’s GPU workflow.

[

Resource Synchronization](/documentation/Metal/resource-synchronization)

Prevent multiple commands that can access the same resources simultaneously by coordinating those accesses with barriers, fences, or events.

[

Synchronizing resource accesses within a single pass with an intrapass barrier](/documentation/Metal/synchronizing-resource-accesses-within-a-single-pass-with-an-intrapass-barrier)

Resolve resource access conflicts between stages within a single pass by adding an intrapass barrier.

[

Synchronizing resource accesses between multiple passes with a fence](/documentation/Metal/synchronizing-resource-accesses-between-multiple-passes-with-a-fence)

Resolve resource access conflicts between multiple passes within a single command queue by signaling a fence in one pass and waiting for it in another.

[

Synchronizing resource accesses with earlier passes with a consumer-based queue barrier](/documentation/Metal/synchronizing-resource-accesses-with-earlier-passes-with-a-consumer-based-queue-barrier)

Resolve resource access conflicts between multiple passes within a single command queue by creating a consumer-based intraqueue barrier.

[

Synchronizing resource accesses with subsequent passes with a producer-based queue barrier](/documentation/Metal/synchronizing-resource-accesses-with-subsequent-passes-with-a-producer-based-queue-barrier)

Resolve resource access conflicts between multiple passes within a single command queue by creating a producer-based intraqueue barrier.

### [Parental controls and safety](/documentation/updates/wwdc2025#Parental-controls-and-safety)

[

PermissionKit](/documentation/PermissionKit)

Create communication experiences between a child and their parent or guardian.

Beta

[

DeclaredAgeRange](/documentation/DeclaredAgeRange)

Create age-appropriate experiences in your app by asking people to share their age range.

Beta

```swift
```swift
```swift
class SCVideoStreamAnalyzer
```
```

An object that monitors a stream of video by analyzing frames for sensitive content.

Beta
```

### [Security and privacy](/documentation/updates/wwdc2025#Security-and-privacy)

[

Enabling enhanced security for your app](/documentation/Xcode/enabling-enhanced-security-for-your-app)

Detect out-of-bounds memory access, use of freed memory, and other potential vulnerabilities.

[

Creating extensions with enhanced security](/documentation/Xcode/creating-extensions-with-enhanced-security)

Reduce opportunities for an attacker to target your app through its extensions.

### [Spatial computing with visionOS](/documentation/updates/wwdc2025#Spatial-computing-with-visionOS)

[

Immersive Media Support](/documentation/ImmersiveMediaSupport)

Read and write essential Apple Immersive Video metadata.

Beta

[

Authoring Apple Immersive Video](/documentation/ImmersiveMediaSupport/authoring-apple-immersive-video)

Prepare and package immersive video content for delivery.

Beta

[

Adopting best practices for persistent UI](/documentation/visionOS/adopting-best-practices-for-scene-restoration)

Create persistent and contextually relevant spatial experiences by managing scene restoration, customizing window behaviors, and surface snapping data.

[

Presenting images in RealityKit](/documentation/RealityKit/presenting-images-in-realitykit)

Create and display spatial scenes in RealityKit.

[

Tracking accessories in volumetric windows](/documentation/ARKit/tracking-accessories-in-volumetric-windows)

Translate the position and velocity of tracked handheld accessories to throw virtual balls at a stack of cans.

Beta

[

Configure your visionOS app for sharing with people nearby](/documentation/GroupActivities/configure-your-app-for-sharing-with-people-nearby)

Create shared experiences for people wearing Vision Pro in the same room and those on FaceTime.

### [SwiftUI, UIKit, and AppKit](/documentation/updates/wwdc2025#SwiftUI-UIKit-and-AppKit)

[

Liquid Glass](/documentation/TechnologyOverviews/liquid-glass)

Learn how to design and develop beautiful interfaces that leverage Liquid Glass.

[

Adopting Liquid Glass](/documentation/TechnologyOverviews/adopting-liquid-glass)

Find out how to bring the new material to your app.

[

Landmarks: Building an app with Liquid Glass](/documentation/SwiftUI/Landmarks-Building-an-app-with-Liquid-Glass)

Enhance your app experience with system-provided and custom Liquid Glass.

Beta

[

Landmarks: Displaying custom activity badges](/documentation/SwiftUI/Landmarks-Displaying-custom-activity-badges)

Provide people with a way to mark their adventures by displaying animated custom activity badges.

Beta

[

Landmarks: Refining the system provided Liquid Glass effect in toolbars](/documentation/SwiftUI/Landmarks-Refining-the-system-provided-glass-effect-in-toolbars)

Organize toolbars into related groupings to improve their appearance and utility.

Beta

[

Landmarks: Extending horizontal scrolling under a sidebar or inspector](/documentation/SwiftUI/Landmarks-Extending-horizontal-scrolling-under-a-sidebar-or-inspector)

Improve your horizontal scrollbar’s appearance by extending it under a sidebar or inspector.

Beta

[

Applying Liquid Glass to custom views](/documentation/SwiftUI/Applying-Liquid-Glass-to-custom-views)

Configure, combine, and morph views using Liquid Glass effects.

[

Building and customizing the menu bar with SwiftUI](/documentation/SwiftUI/Building-and-customizing-the-menu-bar-with-SwiftUI)

Provide a seamless, cross-platform user experience by building a native menu bar for iPadOS and macOS.

[

Populating SwiftUI menus with adaptive controls](/documentation/SwiftUI/Populating-SwiftUI-menus-with-adaptive-controls)

Improve your app by populating menus with controls and organizing your content intuitively.

[

Building rich SwiftUI text experiences](/documentation/SwiftUI/building-rich-swiftui-text-experiences)

Build an editor for formatted text using SwiftUI text editor views and attributed strings.

Beta

### [System services](/documentation/updates/wwdc2025#System-services)

[

Wi-Fi Aware](/documentation/WiFiAware)

Securely pair and connect to external devices over peer-to-peer Wi-Fi.

Beta

[

Connecting devices for peer-to-peer Wi-Fi](/documentation/WiFiAware/Connecting-paired-devices)

Make outgoing and accept incoming secure connections with paired devices.

[

Building peer-to-peer apps](/documentation/WiFiAware/Building-peer-to-peer-apps)

Communicate with nearby devices over a secure, high-throughput, low-latency connection by using Wi-Fi Aware.

[

Adopting Wi-Fi Aware](/documentation/WiFiAware/Adopting-Wi-Fi-Aware)

Add entitlements and declare your app’s services.

[

AlarmKit](/documentation/AlarmKit)

Schedule prominent alarms and countdowns to help people manage their time.

Beta

[

Scheduling an alarm with AlarmKit](/documentation/AlarmKit/scheduling-an-alarm-with-alarmkit)

Create prominent alerts at specified dates for your iOS app.

Beta

[

WirelessInsights](/documentation/WirelessInsights)

Receive notifications for anticipated changes in cellular data service conditions.

Beta

[

RelevanceKit](/documentation/RelevanceKit)

Provide on-device intelligence with contextual clues that increase your widget’s visibility on Apple Watch.

Beta

[

TelephonyMessagingKit](/documentation/TelephonyMessagingKit)

Send and receive standards-based messages over cellular networks.

Beta

## [See Also](/documentation/updates/wwdc2025#see-also)

### [WWDC](/documentation/updates/wwdc2025#WWDC)

[

API Reference

WWDC24](/documentation/updates/wwdc2024)

Highlights of new technologies introduced at WWDC24.

[

API Reference

WWDC23](/documentation/updates/wwdc2023)

Highlights of new technologies introduced at WWDC23.

[

API Reference

WWDC22](/documentation/updates/wwdc2022)

Highlights of new technologies introduced at WWDC22.

[

API Reference

WWDC21](/documentation/updates/wwdc2021)

Highlights of new technologies introduced at WWDC21.