

- UIKit
- UIScene
-  didActivateNotification 

Type Property

# didActivateNotification

A notification that indicates that the scene is now onscreen and responding to user events.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.1+tvOS 13.0+visionOS 1.0+

``` source
nonisolated
class let didActivateNotification: NSNotification.Name
```

## Discussion

Use this notification to prepare your scene to be onscreen. UIKit posts this notification after loading the interface for your scene, but before that interface appears onscreen. Use it to refresh the contents of views, start timers, or increase frame rates for your UI. UIKit places the scene object in the object property of the notification.

UIKit also calls the sceneDidBecomeActive(_:) method of your scene delegate object.

For more information on what to do when your app becomes active, see Preparing your UI to run in the foreground.

## See Also

### Responding to life cycle notifications

class let willConnectNotification: NSNotification.Name

A notification that indicates that UIKit added a scene to your app.

class let didDisconnectNotification: NSNotification.Name

A notification that indicates that UIKit removed a scene from your app.

class let willEnterForegroundNotification: NSNotification.Name

A notification that indicates that a scene is about to begin running in the foreground and become visible to the user.

class let willDeactivateNotification: NSNotification.Name

A notification that indicates that the scene is about to resign the active state and stop responding to user events.

class let didEnterBackgroundNotification: NSNotification.Name

A notification that indicates that the scene is running in the background and is no longer onscreen.

