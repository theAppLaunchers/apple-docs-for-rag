Collection

*   [Xcode](/documentation/xcode)
*   Capabilities

# Capabilities

Enable services that Apple provides, such as In-App Purchase, Push Notifications, Apple Pay, iCloud, and many others.

## [Overview](/documentation/Xcode/capabilities#overview)

Capabilities simplify the configuration process for many of Apple’s services, some of which require you to configure specific entitlements or change your app’s provisioning profile. When you add a capability to an app or other target in your project, Xcode automatically configures that target to use the corresponding service. For example, Xcode might add a required entitlement to a new entitlements file and configure the project to use those entitlements. When Xcode needs you to provide additional information, it presents a simplified UI for you to specify that information.

![A screenshot of Xcode’s Capabilities library. On the left is a list of available capabilities where you can double-click or drag a capability to add it to the selected target. On the right is a description of the selected capability. There’s a text box at the top that allows you to filter the list of capabilities.](https://docs-assets.developer.apple.com/published/2615efe10594368ecb5a0ed009c3a509/capabilities%402x.png)

Note

You add most capabilities directly from Xcode, but some app services — such as Game Center and In-App Purchase — require additional setup in App Store Connect and your developer account. For more information, see the documentation below for the specific capability.

## [Topics](/documentation/Xcode/capabilities#topics)

### [Essentials](/documentation/Xcode/capabilities#Essentials)

[

Adding capabilities to your app](/documentation/xcode/adding-capabilities-to-your-app)

Configure your target to include and customize capabilities that provide access to Apple’s app services.

### [App execution](/documentation/Xcode/capabilities#App-execution)

[

Configuring background execution modes](/documentation/xcode/configuring-background-execution-modes)

Indicate the background services your app requires to continue executing in the background in iOS, iPadOS, tvOS, visionOS, and watchOS.

[

Configuring custom fonts](/documentation/xcode/configuring-custom-fonts)

Register your app as a provider or consumer of systemwide custom fonts.

[

Configuring game controllers](/documentation/xcode/configuring-game-controllers)

Enhance gameplay input by enabling the discovery, configuration, and use of physical game controllers.

[

Configuring Maps support](/documentation/xcode/configuring-maps-support)

Register your iOS routing app to provide point-to-point directions to Maps and other apps.

[

Configuring Siri support](/documentation/xcode/configuring-siri-support)

Enable your app and its Intents extension to resolve, confirm, and handle user-driven Siri requests for your app’s services.

### [Commerce](/documentation/Xcode/capabilities#Commerce)

[

Configuring Apple Pay support](/documentation/xcode/configuring-apple-pay-support)

Process payments in your app using the payment information the user stores on their device.

[

Configuring Sign in with Apple support](/documentation/xcode/configuring-sign-in-with-apple)

Allow users to create an account and sign in to your app with their Apple Account.

[

Configuring Wallet support](/documentation/xcode/configuring-wallet-support)

Access the user’s Wallet to add, update, and display your app’s passes.

### [Data management](/documentation/Xcode/capabilities#Data-management)

[

Configuring an associated domain](/documentation/xcode/configuring-an-associated-domain)

Create a two-way association between your app and your website to enable universal links, Handoff, App Clips, and shared web credentials.

[

Configuring app groups](/documentation/xcode/configuring-app-groups)

Enable communication and data sharing between multiple installed apps created by the same developer.

[

Configuring iCloud services](/documentation/xcode/configuring-icloud-services)

Share user or app data among multiple instances of your app running on different devices.

### [Network](/documentation/Xcode/capabilities#Network)

[

Configuring network extensions](/documentation/xcode/configuring-network-extensions)

Customize the various capabilities of your app’s networking stack, such as proxying DNS queries or creating packet tunnels.

[

Registering your app with APNs](/documentation/UserNotifications/registering-your-app-with-apns)

Communicate with Apple Push Notification service (APNs) and receive a unique device token that identifies your app.

[

Configuring Group Activities](/documentation/xcode/configuring-group-activities)

Leverage FaceTime infrastructure to create coordinated experiences users can share.

[

Configuring media device discovery](/documentation/xcode/configuring-media-device-discovery)

Add a third-party media device or protocol as a streaming option in the same system menu as AirPlay.

### [Security](/documentation/Xcode/capabilities#Security)

[

Configuring the hardened runtime](/documentation/xcode/configuring-the-hardened-runtime)

Protect the runtime integrity of your macOS app by restricting access to sensitive resources and preventing common exploits.

[

Configuring the macOS App Sandbox](/documentation/xcode/configuring-the-macos-app-sandbox)

Protect system resources and user data from compromised apps by restricting access to the file system, network connections, and more.

[

Configuring keychain sharing](/documentation/xcode/configuring-keychain-sharing)

Share keychain items between multiple apps belonging to the same developer.

### [User data](/documentation/Xcode/capabilities#User-data)

[

Configuring HealthKit access](/documentation/xcode/configuring-healthkit-access)

Read and write health and activity data in the Health app.

[

Configuring HomeKit access](/documentation/xcode/configuring-homekit-access)

Discover compatible accessories and communicate with configured accessories and services to perform actions.

## [See Also](/documentation/Xcode/capabilities#see-also)

### [Xcode IDE](/documentation/Xcode/capabilities#Xcode-IDE)

[

API Reference

Projects and workspaces](/documentation/xcode/projects-and-workspaces)

Manage the code and resources you use to build apps, libraries, and other software for Apple platforms.

[

API Reference

Source control management](/documentation/xcode/source-control-management)

Back up your files, collaborate with others, and tag your releases with source control support in Xcode.

[

API Reference

Build system](/documentation/xcode/build-system)

Compile your code into a binary format, and customize your project settings to build your code.