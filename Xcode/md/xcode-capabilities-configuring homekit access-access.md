

- Xcode
- Capabilities
-  Configuring HomeKit access 

Article

# Configuring HomeKit access

Discover compatible accessories and communicate with configured accessories and services to perform actions.

## Overview

Apps that integrate with HomeKit can securely connect to a user’s home automation network and access compatible accessories. After an app connects to an accessory, it can read and update that accessory’s state, for example, by changing the ambient color of a smart light bulb.

To enable your app to control the user’s compatible accessories, you must add the HomeKit capability to your app’s target and include a short description of the app’s functionality in its target’s `Info.plist` file.

### Add the HomeKit capability to your target

Follow the steps in Add a capability to add the capability to your app’s target; be sure to select the HomeKit capability from Xcode’s Capabilities library. For watchOS apps with separate WatchKit extensions, you must add the capability to the WatchKit Extension target. The capability isn’t available for macOS.

After you add the HomeKit capability, Xcode links the `HomeKit` framework to your target and updates its entitlements file to include the HomeKit Entitlement. If Xcode automatically manages the signing of your app, it also enables HomeKit for your app’s App ID.

### Request access to a home automation network

To help protect the security and privacy of the user’s home automation network, your app requires the user’s explicit permission before it can control HomeKit accessories on that network. The system prompts the user for their permission the first time your app uses the HomeKit framework, which is when you initialize HMHomeManager.

The App Store requires your app to include a *purpose string*, which accurately and concisely describes the reasons the app needs access to the user’s network. The system displays this information to the user when requesting their permission, which helps them make an informed decision. Follow these steps to add the purpose string to your target:

1.  In the Project navigator, select your target’s `Info.plist` file.

2.  Move the mouse pointer over the “Information Property List” key.

3.  Click the Add button (+) that appears.

4.  Choose “Privacy - HomeKit Usage Description” from the drop-down menu.

5.  Double-click the Value column to the right of the key and enter your app’s purpose string.

Important

Apps that enable Homekit but don’t include a purpose string crash when attempting to use the framework’s APIs.

Remember that the user can revoke their permission at any time in the Settings app, and your app must respond to this accordingly. You can check your app’s current authorization status by accessing the authorizationStatus property. HomeKit also returns a homeAccessNotAuthorized error if your app attempts to make an unauthorized call to any of the framework’s APIs.

### Install the HomeKit accessory simulator

Integrating with HomeKit doesn’t require you to have physical access to each of the accessories that your app supports. Instead, you can install the HomeKit Accessory Simulator and simulate each of those accessories. To install the simulator, follow these steps:

1.  Open the Signing & Capabilities tab in your target’s project editor.

2.  Find the HomeKit capability.

3.  Click the Download HomeKit Simulator button.

4.  On the More Downloads webpage that opens, find and download the latest “Additional Tools for Xcode” DMG file. Your browser may ask you to sign in to your Apple developer account first.

5.  After the DMG file downloads, double-click it to mount the disk image in Finder.

6.  Open the Hardware folder.

7.  Drag the HomeKit Accessory Simulator app to your Mac’s Applications folder.

Use the simulator to add and remove simulated HomeKit accessories, services, and characteristics, and to simulate networked cameras and video doorbells by leveraging your Mac’s camera. For more information, see the Add Accessories, Services, and Characteristics section of Testing Your App with the HomeKit Accessory Simulator.

## See Also

### User data

Configuring HealthKit access

Read and write health and activity data in the Health app.

