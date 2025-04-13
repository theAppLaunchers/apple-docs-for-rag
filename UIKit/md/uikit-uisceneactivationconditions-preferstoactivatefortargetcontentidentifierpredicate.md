

- UIKit
- UISceneActivationConditions
-  prefersToActivateForTargetContentIdentifierPredicate 

Instance Property

# prefersToActivateForTargetContentIdentifierPredicate

The set of conditions for which UIKit chooses to activate this scene over others.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.1+tvOS 13.0+visionOS 1.0+

``` source
@NSCopying @MainActor
var prefersToActivateForTargetContentIdentifierPredicate: NSPredicate { get set }
```

## Discussion

Use this property to specify which tasks you want this scene to handle. UIKit evaluates your predicate against the targetContentIdentifier property of the object causing the activation of the scene. Many different objects contain target content identifiers, including NSUserActivity, UNNotificationContent, and UIApplicationShortcutItem.

UIKit must be able to evaluate your predicate’s conditions outside the scope of your app, so don’t include conditions that require dynamic evaluation. For example, don’t include key paths in your predicate and don’t create predicates that evaluate conditions using selectors or blocks. The default value of this property is a predicate that always evaluates to the value false.

## See Also

### Specifying the conditions

var canActivateForTargetContentIdentifierPredicate: NSPredicate

Conditions for which UIKit can activate the scene if a better alternative doesn’t exist.

