

- CarPlay
-  CPTemplateApplicationDashboardSceneDelegate 

Protocol

# CPTemplateApplicationDashboardSceneDelegate

The methods for responding to the life-cycle events of your navigation app’s dashboard scene.

iOS 13.4+iPadOS 13.4+Mac Catalyst 13.4+

``` source
protocol CPTemplateApplicationDashboardSceneDelegate : UISceneDelegate
```

## Overview

This protocol defines methods that CarPlay calls when the scene connects and disconnects, and your implementation provides the appropriate behavior when these events occur. For example, setting the window’s root view controller when CarPlay connects your navigation app’s dashboard scene.

You don’t create instances of your dashboard scene delegate directly. Instead, you specify the name of the class as part of the CarPlay scene configuration you add to your `Info.plist` file—see the example below—or that you return from your app delegate’s application(_:configurationForConnecting:options:) method.

```
CPTemplateApplicationDashboardSceneSessionRoleApplication

        UISceneClassName
        CPTemplateApplicationDashboardScene
        UISceneConfigurationName
        MyCarPlayDashboardSceneConfiguration

        UISceneDelegateClassName
        MyCarPlayDashboardSceneDelegate 

```

## Topics

### Responding to the Scene Life Cycle

func templateApplicationDashboardScene(CPTemplateApplicationDashboardScene, didConnect: CPDashboardController, to: UIWindow)

Tells the delegate about the addition of a CarPlay Dashboard scene to your navigation app.

func templateApplicationDashboardScene(CPTemplateApplicationDashboardScene, didDisconnect: CPDashboardController, from: UIWindow)

Tells the delegate when CarPlay removes the dashboard scene from your navigation app.

## Relationships

### Inherits From

- NSObjectProtocol
- UISceneDelegate

## See Also

### Navigation

Integrating CarPlay with Your Navigation App

Configure your navigation app to work with CarPlay by displaying your custom map and directions.

class CPTemplateApplicationDashboardScene

A CarPlay scene that controls your app’s dashboard navigation window.

class CPMapTemplate

A template that displays a navigation overlay that your app draws on the map.

class CPSearchTemplate

A template that provides the ability to search for a destination and see a list of search results.

class CPVoiceControlTemplate

A template that displays a voice control indicator during audio input.

