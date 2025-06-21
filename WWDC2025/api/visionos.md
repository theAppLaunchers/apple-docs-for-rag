![](https://docs-assets.developer.apple.com/published/77dc6a0821bfb2da8db4a3b2033e6f6b/headset-orange.svg)

# visionOS

Create a new universe of apps and games for Apple Vision Pro.

visionOS 1.0+

## [Overview](/documentation/visionOS#Overview)

visionOS is the operating system that powers Apple Vision Pro. Use visionOS together with familiar tools and technologies to build immersive apps and games for spatial computing.

![Three scenes from visionOS apps that show the Music app, a close-up of the tools associated with a window, and a photo browser.](https://docs-assets.developer.apple.com/published/230b02516973a1e9ed5e1ce8f8e62ccc/overview%402x.png)

Developing for visionOS requires a Mac with Apple silicon. Create new apps using SwiftUI to take full advantage of the spectrum of immersion available in visionOS. If you have an existing iPad or iPhone app, add the visionOS destination to your app’s target to gain access to the standard system appearance, and add platform-specific features to create a compelling experience. To provide continuous access to your content in the meantime, deliver a compatible version of your app that runs in visionOS.

### [Expand your app into immersive spaces](/documentation/visionOS#Expand-your-app-into-immersive-spaces)

Start with a familiar window-based experience to introduce people to your content. From there, add [SwiftUI](/documentation/SwiftUI) scene types specific to visionOS, such as volumes and spaces. These scene types let you incorporate depth, 3D objects, and immersive experiences.

Build your app’s 3D content with [RealityKit](/documentation/RealityKit) and Reality Composer Pro, and display it with a [`RealityView`](/documentation/RealityKit/RealityView). In an immersive experience, use [ARKit](/documentation/ARKit) to integrate your content with the person’s surroundings.

![An illustration that shows a person wearing Apple Vision Pro and looking at three windows and a volume in the space in front of them.](https://docs-assets.developer.apple.com/published/d369f4df61db5fbc2f996ce515e281ea/shared-spaces%402x.png)

### [Explore new kinds of interaction](/documentation/visionOS#Explore-new-kinds-of-interaction)

People can select an element by looking at it and tapping their fingers together. They can also pinch, drag, zoom, and rotate objects using specific hand gestures. [SwiftUI](/documentation/SwiftUI) provides built-in support for these standard gestures, so rely on them for most of your app’s input. When you want to go beyond the standard gestures, use [ARKit](/documentation/ARKit) to create custom gestures.

![An illustration that shows a person touching their thumb and index finger together to create a tap gesture.](https://docs-assets.developer.apple.com/published/f70a43934f0de46e6728061e0317c5fc/tap%402x.png)

Tap to select

![An illustration that shows a person making tap gestures with both hands and then rotating their hands around a central point.](https://docs-assets.developer.apple.com/published/f6c70e507db9aa720d35fc18245d203e/rotate%402x.png)

Pinch to rotate

![An illustration that shows a person touching their thumb and index finger together to select a cube, and then using hand motions to manipulate the cube's position and orientation.](https://docs-assets.developer.apple.com/published/edd50244a975b4ef4e691c7976b34e11/direct-manipulation%402x.png)

Manipulate objects

![An illustration that shows an object sitting in the palm of someone's hand.](https://docs-assets.developer.apple.com/published/ffa3cd598105c3a4fc6813929f8131db/custom%402x.png)

Create custom gestures

### [Dive into featured sample apps](/documentation/visionOS#Dive-into-featured-sample-apps)

Explore the core concepts for all visionOS apps with Hello World. Understand how to detect custom gestures using ARKit with Happy Beam. Discover streaming 2D and stereoscopic media with Destination Video. And learn how to build 3D scenes with RealityKit and Reality Composer Pro with Diorama and Swift Splash.

[

![An image showing the Bright Angel Trail hike being started and a hiker starting to move down the trail.](https://docs-assets.developer.apple.com/published/0d46a37cd4649de679c0e54d0d99cc85/Canyon-Crosser-PageImage-card.png)

Canyon Crosser: Building a volumetric hike-planning app

Create a hike planning app using SwiftUI and RealityKit.

View sample code

](/documentation/visionos/canyon-crosser-building-a-volumetric-hike-planning-app)

[

![A screenshot of a towering butte presented in a volume within a mixed reality space running inside the visionOS simulator.](https://docs-assets.developer.apple.com/published/82f8c7674c19f24265584000b0786e9e/petite-asteroids-PageImage-card%402x.png)

Petite Asteroids: Building a volumetric visionOS game

Use the latest RealityKit APIs to create a beautiful video game for visionOS.

View sample code

](/documentation/visionos/petite-asteroids-building-a-volumetric-visionos-game)

[

![](https://docs-assets.developer.apple.com/published/770e1d0451ba3b86de3b05eb0ce728b7/Hello-World-intro%402x.png)

Hello World

Use windows, volumes, and immersive spaces to teach people about the Earth.

View sample code

](/documentation/visionos/world)

[

![A screenshot from the Apple Vision Pro simulator with a single floating window. The window contains a robot on the right side, and controls to customize the robots appearance on the left.](https://docs-assets.developer.apple.com/published/d9f7d85cd82f76e6fd53df7302f0424a/BOT-anist-PageImage-card%402x.png)

BOT-anist

Build a multiplatform app that uses windows, volumes, and animations to create a robot botanist’s greenhouse.

View sample code

](/documentation/visionos/bot-anist)

[

![An image showing Destination Video on visionOS.](https://docs-assets.developer.apple.com/published/648c665254129674ce04bbc64dbeeb2d/Destination-Video-intro%402x.png)

Destination Video

Leverage SwiftUI to build an immersive media experience in a multiplatform app.

View sample code

](/documentation/visionos/destination-video)

[

![A screenshot showing the Happy Beam game. A player makes a heart gesture with their hands, a beam projects from it aimed at nearby clouds, and a scoreboard window shows seven points.](https://docs-assets.developer.apple.com/published/52b497b6d705af322726d7371dee6ddd/Happy-Beam-intro%402x.png)

Happy Beam

Leverage a Full Space to create a fun game using ARKit.

View sample code

](/documentation/visionos/happybeam)

[

![A screenshot showing a virtual trail map diorama in a living room setting.](https://docs-assets.developer.apple.com/published/80d69390976dca0e5d70a493312d475a/Diorama-intro%402x.png)

Diorama

Design scenes for your visionOS app using Reality Composer Pro.

View sample code

](/documentation/visionos/diorama)

[

![](https://docs-assets.developer.apple.com/published/b5da9880ce266b0858346d694e3a7018/Swift-Splash-intro%402x.png)

Swift Splash

Use RealityKit to create an interactive ride in visionOS.

View sample code

](/documentation/visionos/swift-splash)

## [Topics](/documentation/visionOS#topics)

### [App construction](/documentation/visionOS#App-construction)

[

Creating your first visionOS app](/documentation/visionos/creating-your-first-visionos-app)

Build a new visionOS app using SwiftUI and add platform-specific features.

[

Adding 3D content to your app](/documentation/visionos/adding-3d-content-to-your-app)

Add depth and dimension to your visionOS app and discover how to incorporate your app’s content into a person’s surroundings.

[

Creating fully immersive experiences in your app](/documentation/visionos/creating-fully-immersive-experiences)

Build fully immersive experiences by combining spaces with content you create using RealityKit or Metal.

[

Drawing sharp layer-based content in visionOS](/documentation/visionos/drawing-sharp-layer-based-content)

Deliver text and vector images at multiple resolutions from custom Core Animation layers in visionOS.

[

API Reference

Introductory visionOS samples](/documentation/visionos/introductory-visionos-samples)

Learn the fundamentals of building apps for visionOS with beginner-friendly sample code projects.

### [Design](/documentation/visionOS#Design)

[

Designing for visionOS](/design/Human-Interface-Guidelines/designing-for-visionos)

When people wear Apple Vision Pro, they enter an infinite 3D space where they can engage with your app or game while staying connected to their surroundings.

[

Adopting best practices for privacy and user preferences](/documentation/visionos/adopting-best-practices-for-privacy)

Minimize your use of sensitive information and provide a clear statement of what information you do use and how you use it.

[

Improving accessibility support in your visionOS app](/documentation/visionos/improving-accessibility-support-in-your-app)

Update your code to ensure everyone can access your app’s content in visionOS.

### [SwiftUI](/documentation/visionOS#SwiftUI)

[

Canyon Crosser: Building a volumetric hike-planning app](/documentation/visionos/canyon-crosser-building-a-volumetric-hike-planning-app)

Create a hike planning app using SwiftUI and RealityKit.

[

Hello World](/documentation/visionos/world)

Use windows, volumes, and immersive spaces to teach people about the Earth.

[

Presenting windows and spaces](/documentation/visionos/presenting-windows-and-spaces)

Open and close the scenes that make up your app’s interface.

[

Positioning and sizing windows](/documentation/visionos/positioning-and-sizing-windows)

Influence the initial geometry of windows that your app presents.

[

Adopting best practices for persistent UI](/documentation/visionos/adopting-best-practices-for-scene-restoration)

Create persistent and contextually relevant spatial experiences by managing scene restoration, customizing window behaviors, and surface snapping data.

### [RealityKit and Reality Composer Pro](/documentation/visionOS#RealityKit-and-Reality-Composer-Pro)

[

Petite Asteroids: Building a volumetric visionOS game](/documentation/visionos/petite-asteroids-building-a-volumetric-visionos-game)

Use the latest RealityKit APIs to create a beautiful video game for visionOS.

[

BOT-anist](/documentation/visionos/bot-anist)

Build a multiplatform app that uses windows, volumes, and animations to create a robot botanist’s greenhouse.

[

Swift Splash](/documentation/visionos/swift-splash)

Use RealityKit to create an interactive ride in visionOS.

[

Diorama](/documentation/visionos/diorama)

Design scenes for your visionOS app using Reality Composer Pro.

[

Building an immersive media viewing experience](/documentation/visionos/building-an-immersive-media-viewing-experience)

Add a deeper level of immersion to media playback in your app with RealityKit and Reality Composer Pro.

[

Enabling video reflections in an immersive environment](/documentation/visionos/enabling-video-reflections-in-an-immersive-environment)

Create a more immersive experience by adding video reflections in a custom environment.

[

Combining 2D and 3D views in an immersive app](/documentation/RealityKit/combining-2d-and-3d-views-in-an-immersive-app)

Use attachments to place 2D content relative to 3D content in your visionOS app.

[

Understanding the modular architecture of RealityKit](/documentation/visionos/understanding-the-realitykit-modular-architecture)

Learn how everything fits together in RealityKit.

[

Using transforms to move, scale, and rotate entities](/documentation/visionos/understanding-transforms)

Learn how to use Transforms to move, scale, and rotate entities in RealityKit.

[

Designing RealityKit content with Reality Composer Pro](/documentation/visionos/designing-realitykit-content-with-reality-composer-pro)

Design RealityKit scenes for your visionOS app.

[

Capturing screenshots and video from Apple Vision Pro for 2D viewing](/documentation/visionos/capturing-screenshots-and-video-from-your-apple-vision-pro-for-2d-viewing)

Create screenshots and record high-quality video of your visionOS app and its surroundings for app previews.

[

Implementing object tracking in your visionOS app](/documentation/visionos/implementing-object-tracking-in-your-visionos-app)

Create engaging interactions by training models to recognize and track real-world objects in your app.

[

Placing entities using head and device transform](/documentation/visionos/placing-entities-using-head-and-device-transform)

Query and react to changes in the position and rotation of Apple Vision Pro.

### [ARKit](/documentation/visionOS#ARKit)

[

Happy Beam](/documentation/visionos/happybeam)

Leverage a Full Space to create a fun game using ARKit.

[

Setting up access to ARKit data](/documentation/visionos/setting-up-access-to-arkit-data)

Check whether your app can use ARKit and respect people’s privacy.

[

Incorporating real-world surroundings in an immersive experience](/documentation/visionos/incorporating-real-world-surroundings-in-an-immersive-experience)

Create an immersive experience by making your app’s content respond to the local shape of the world.

[

Placing content on detected planes](/documentation/visionos/placing-content-on-detected-planes)

Detect horizontal surfaces like tables and floors, as well as vertical planes like walls and doors.

[

Tracking specific points in world space](/documentation/visionos/tracking-points-in-world-space)

Retrieve the position and orientation of anchors your app stores in ARKit.

[

Tracking preregistered images in 3D space](/documentation/visionos/tracking-images-in-3d-space)

Place content based on the current position of a known image in a person’s surroundings.

[

Exploring object tracking with ARKit](/documentation/visionos/exploring_object_tracking_with_arkit)

Find and track real-world objects in visionOS using reference objects trained with Create ML.

[

Object tracking with Reality Composer Pro experiences](/documentation/visionos/object-tracking-with-reality-composer-pro-experiences)

Use object tracking in visionOS to attach digital content to real objects to create engaging experiences.

[

Building local experiences with room tracking](/documentation/visionos/building_local_experiences_with_room_tracking)

Use room tracking in visionOS to provide custom interactions with physical spaces.

[

Placing entities using head and device transform](/documentation/visionos/placing-entities-using-head-and-device-transform)

Query and react to changes in the position and rotation of Apple Vision Pro.

### [Video playback](/documentation/visionOS#Video-playback)

[

Destination Video](/documentation/visionos/destination-video)

Leverage SwiftUI to build an immersive media experience in a multiplatform app.

[

Playing immersive media with RealityKit](/documentation/visionos/playing-immersive-media-with-realitykit)

Create an immersive video playback experience with RealityKit.

[

Creating a multiview video playback experience in visionOS](/documentation/AVKit/creating-a-multiview-video-playback-experience-in-visionos)

Build an interface that plays multiple videos simultaneously and handles transitions to different experience types gracefully.

[

Configuring your app for media playback](/documentation/AVFoundation/configuring-your-app-for-media-playback)

Configure apps to enable standard media playback behavior.

[

Adopting the system player interface in visionOS](/documentation/AVKit/adopting-the-system-player-interface-in-visionos)

Provide an optimized viewing experience for watching 3D video content.

[

Controlling the transport behavior of a player](/documentation/AVFoundation/controlling-the-transport-behavior-of-a-player)

Play, pause, and seek through a media presentation.

[

Monitoring playback progress in your app](/documentation/AVFoundation/monitoring-playback-progress-in-your-app)

Observe the playback of a media asset to update your app’s user-interface state.

[

Trimming and exporting media in visionOS](/documentation/AVKit/trimming-and-exporting-media-in-visionos)

Display standard controls in your app to edit the timeline of the currently playing media.

### [Xcode and Simulator](/documentation/visionOS#Xcode-and-Simulator)

[

Configuring your app icon using an asset catalog](/documentation/Xcode/configuring-your-app-icon)

Add app icon variations to an asset catalog that represents your app in places such as the App Store, the Home Screen, Settings, and search results.

[

Diagnosing and resolving bugs in your running app](/documentation/Xcode/diagnosing-and-resolving-bugs-in-your-running-app)

Inspect your app to isolate bugs, locate crashes, identify excess system-resource usage, visualize memory bugs, and investigate problems in its appearance.

[

Diagnosing issues in the appearance of a running app](/documentation/Xcode/diagnosing-issues-in-the-appearance-of-your-running-app)

Inspect your running app to investigate issues in the appearance and placement of the content it displays.

[

Running your app in Simulator or on a device](/documentation/Xcode/running-your-app-in-simulator-or-on-a-device)

Launch your app in a simulated iOS, iPadOS, tvOS, visionOS, or watchOS device, or on a device connected to a Mac.

[

Interacting with your app in the visionOS simulator](/documentation/Xcode/interacting-with-your-app-in-the-visionos-simulator)

Use your Mac to navigate spaces and control interactions with your visionOS apps in Simulator.

### [Performance](/documentation/visionOS#Performance)

[

Creating a performance plan for your visionOS app](/documentation/visionos/creating-a-performance-plan-for-visionos-app)

Identify your app’s performance and power goals and create a plan to measure and assess them.

[

Analyzing the performance of your visionOS app](/documentation/visionos/analyzing-the-performance-of-your-visionos-app)

Use the RealityKit Trace template in Instruments to evaluate and improve the performance of your visionOS app.

[

Reducing the rendering cost of your UI on visionOS](/documentation/visionos/reducing-the-rendering-cost-of-your-ui-on-visionos)

Optimize your 2D user interface rendering on visionOS.

[

Reducing the rendering cost of RealityKit content on visionOS](/documentation/visionos/reducing-the-rendering-cost-of-realitykit-content-on-visionos)

Optimize your app’s 3D augmented reality content to render efficiently on visionOS.

[

Understanding the visionOS render pipeline](/documentation/visionos/understanding-the-visionos-render-pipeline)

Compare how visionOS handles events and manages its rendering loop differently from other Apple platforms.

### [iOS migration and compatibility](/documentation/visionOS#iOS-migration-and-compatibility)

[

Determining whether to bring your app to visionOS](/documentation/visionos/determining-whether-to-bring-your-app-to-visionos)

Decide whether to bring your existing iPadOS or iOS app to visionOS.

[

Bringing your existing apps to visionOS](/documentation/visionos/bringing-your-app-to-visionos)

Build a version of your iPadOS or iOS app using the visionOS SDK, and update your code for platform differences.

[

Bringing your ARKit app to visionOS](/documentation/visionos/bringing-your-arkit-app-to-visionos)

Update an iPadOS or iOS app that uses ARKit, and provide an equivalent experience in visionOS.

[

Making your existing app compatible with visionOS](/documentation/visionos/making-your-app-compatible-with-visionos)

Modify your iPadOS or iOS app to run successfully in visionOS as a compatible app.

### [Enterprise APIs for visionOS](/documentation/visionOS#Enterprise-APIs-for-visionOS)

[

Accessing the main camera](/documentation/visionos/accessing-the-main-camera)

Add camera-based features to enterprise apps.

[

Building spatial experiences for business apps with enterprise APIs for visionOS](/documentation/visionos/building-spatial-experiences-for-business-apps-with-enterprise-apis)

Grant enhanced sensor access and increased platform control to your visionOS app by using entitlements.

[

Displaying video from connected devices](/documentation/visionos/displaying-video-from-connected-devices)

Show video from devices connected with the Developer Strap in your visionOS app.

[

Locating and decoding barcodes in 3D space](/documentation/visionos/locating-and-decoding-barcodes-in-3d-space)

Create engaging, hands-free experiences based on barcodes in a person’s surroundings.

*   [visionOS](/documentation/visionOS#app-top)
*   [Overview](/documentation/visionOS#Overview)
*   [Expand your app into immersive spaces](/documentation/visionOS#Expand-your-app-into-immersive-spaces)
*   [Explore new kinds of interaction](/documentation/visionOS#Explore-new-kinds-of-interaction)
*   [Dive into featured sample apps](/documentation/visionOS#Dive-into-featured-sample-apps)
*   [Topics](/documentation/visionOS#topics)