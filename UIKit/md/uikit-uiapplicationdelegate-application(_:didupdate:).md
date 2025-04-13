

- UIKit
- UIApplicationDelegate
-  application(\_:didUpdate:) 

Instance Method

# application(\_:didUpdate:)

Tells the delegate that the activity was updated.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.1+tvOSvisionOS 1.0+

``` source
@MainActor
optional func application(
    _ application: UIApplication,
    didUpdate userActivity: NSUserActivity
)
```

## Parameters 

`application`  

Your shared app object.

`userActivity`  

The activity object containing the data associated with the task the user was performing.

## Discussion

This method is called on the main thread when a user activity managed by UIKit has been updated. You can implement this method as a final opportunity to add data to the user activity object.

## See Also

### Continuing user activity and handling quick actions

func application(UIApplication, willContinueUserActivityWithType: String) -> Bool

Tells the delegate if your app takes responsibility for notifying users when a continuation activity takes longer than expected.

func application(UIApplication, continue: NSUserActivity, restorationHandler: ([any UIUserActivityRestoring]?) -> Void) -> Bool

Tells the delegate that the data for continuing an activity is available.

func application(UIApplication, didFailToContinueUserActivityWithType: String, error: any Error)

Tells the delegate that the activity couldn’t be continued.

func application(UIApplication, performActionFor: UIApplicationShortcutItem, completionHandler: (Bool) -> Void)

Tells the delegate that the user selected a Home screen quick action for your app, except when you’ve intercepted the interaction in a launch method.

