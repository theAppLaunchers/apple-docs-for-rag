

- UIKit
- App and environment
-  Multitasking on iPad 

API Collection

# Multitasking on iPad

Implement multitasking APIs to seamlessly integrate your app with iPadOS.

## Overview

While your app runs in the foreground on iPad, other apps are likely to be running alongside it. Being aware of the environment your app may be running in and adopting the multitasking APIs are an essential part of integrating your apps with iPadOS.

The first step to creating a great multitasking experience for your users is to ensure your app can adapt to different window sizes. Start by reading the Adaptivity and Layout section of the Human Interface Guidelines. Also, consider that your app may not be running full screen, but in a smaller window through Slide Over or Split View. Discover your app’s environment with UITraitCollection and adapt to it by using Auto Layout, or by overriding traitCollectionDidChange(_:) in your view controllers or views.

With iPadOS 13 and later, you can choose to allow multiple windows in your app’s UI to run concurrently by setting the UIApplicationSupportsMultipleScenes property list key. Implement Scenes and read Managing your app’s life cycle for an overview of how UISceneDelegate interacts with the system multitasking events.

## Topics

### Adaptivity

class UITraitCollection

A collection of data that represents the environment for an individual element in your app’s user interface.

protocol UITraitEnvironment

A set of methods that makes the iOS interface environment available to your app.

protocol UIAdaptivePresentationControllerDelegate

A set of methods that, in conjunction with a presentation controller, determine how to respond to trait changes in your app.

protocol UIContentContainer

A set of methods for adapting the contents of your view controllers to size and trait changes.

### Scene Management

Scenes

Manage multiple instances of your app’s UI simultaneously, and direct resources to the appropriate instance of your UI.

Supporting multiple windows on iPad

Support side-by-side instances of your app’s interface and create new windows.

## See Also

### iPad

Building a desktop-class iPad app

Optimize your iPad app’s user experience by adopting desktop-class enhancements for multitasking with Stage Manager, document interactions, text editing, search, and more.

Elevating your iPad app with a tab bar and sidebar

Provide a compact, ergonomic tab bar for quick access to key parts of your app, and a sidebar for in-depth navigation.

Supporting desktop-class features in your iPad app

Enhance your iPad app by adding desktop-class features and document support.

