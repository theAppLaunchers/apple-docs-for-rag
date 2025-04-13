

- CarPlay
-  CPTemplateApplicationSceneDelegate 

Protocol

# CPTemplateApplicationSceneDelegate

The methods for responding to the life cycle events of your app’s scene.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.1+

``` source
protocol CPTemplateApplicationSceneDelegate : UISceneDelegate
```

## Mentioned in 

Displaying Content in CarPlay

## Overview

This protocol defines methods that CarPlay calls when the scene connects and disconnects, as well as methods for responding to certain user actions. Use your implementation to provide the appropriate behavior for when these events occur. For example, creating and setting your root template when CarPlay launches your app and connects its scene.

You don’t create instances of your scene delegate directly. Instead, you specify the name of the class as part of the CarPlay scene configuration you add to your `Info.plist` file—see the example below—or that you return from your app delegate’s application(_:configurationForConnecting:options:) method.

```
CPTemplateApplicationSceneSessionRoleApplication

        UISceneClassName
        CPTemplateApplicationScene
        UISceneConfigurationName
        MyCarPlaySceneConfiguration

        UISceneDelegateClassName
        MyCarPlaySceneDelegate 

```

## Topics

### Responding to the Scene Life Cycle

func templateApplicationScene(CPTemplateApplicationScene, didConnect: CPInterfaceController)

Tells the delegate about the addition of a CarPlay scene to the app.

func templateApplicationScene(CPTemplateApplicationScene, didConnect: CPInterfaceController, to: CPWindow)

Tells the delegate about the addition of a CarPlay scene to your navigation app.

func templateApplicationScene(CPTemplateApplicationScene, didDisconnectInterfaceController: CPInterfaceController)

Tells the delegate when CarPlay removes a scene from the app.

func templateApplicationScene(CPTemplateApplicationScene, didDisconnect: CPInterfaceController, from: CPWindow)

Tells the delegate when CarPlay removes a scene from your navigation app.

### Responding to User Actions

func templateApplicationScene(CPTemplateApplicationScene, didSelect: CPManeuver)

Tells the delegate when the user selects a maneuver while the app is in the background.

func templateApplicationScene(CPTemplateApplicationScene, didSelect: CPNavigationAlert)

Tells the delegate when the user selects a navigation alert while the app is in the background.

### Instance Methods

func contentStyleDidChange(UIUserInterfaceStyle)

## Relationships

### Inherits From

- NSObjectProtocol
- UISceneDelegate

## See Also

### CarPlay Integration

Requesting CarPlay Entitlements

Configure your CarPlay-enabled app with the entitlements it requires.

Displaying Content in CarPlay

Use scenes to present your app’s content on the vehicle’s built-in screen.

Supporting Previous Versions of iOS

Make your CarPlay-enabled apps compatible with older system versions, such as iOS 13 and earlier.

Using the CarPlay Simulator

Configure Simulator to run and debug your CarPlay-enabled app.

class CPTemplateApplicationScene

A CarPlay scene that controls your app’s user interface.

class CPSessionConfiguration

An object that provides vehicle properties and configuration for the CarPlay environment.

