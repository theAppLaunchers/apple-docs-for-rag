

- SceneKit
- SCNAction
-  reversed() 

Instance Method

# reversed()

Creates an action that reverses the behavior of another action.

iOSiPadOSMac Catalyst 13.1+macOS 10.10+tvOSvisionOSwatchOS

``` source
func reversed() -> SCNAction
```

## Return Value

A new action that reverses the action’s behavior.

## Discussion

This method always returns an action object; however, not all actions are reversible. When reversed, some actions return an object that either does nothing or performs the same action as the original action. For details on how an action is reversed, see the description of the class method used to create that action.

