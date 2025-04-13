

- UIKit
-  UIApplicationShortcutItem 

Class

# UIApplicationShortcutItem

An application shortcut item, also called a Home Screen dynamic quick action, that specifies a user-initiated action for your app.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+visionOS 1.0+

``` source
class UIApplicationShortcutItem
```

## Overview

On a device that supports 3D Touch, a person invokes the quick action by pressing your app’s icon on the Home Screen and then selecting the quick action’s title. Your app delegate receives and handles the quick action.

You must specify the characteristics of your UIApplicationShortcutItem instances during initialization, before you register them with your app object. The quick actions you’ve registered with your app object are immutable.

### Register an array of dynamic quick actions with your app

To register an array of Home Screen dynamic quick actions, set the value of your shared app object’s shortcutItems property with an NSArray instance containing your defined dynamic Home Screen quick actions.

### Change your app’s dynamic quick actions

To change your app’s Home Screen dynamic quick actions, replace your app object’s shortcutItems array by setting a new value for the property. As a convenience for working with registered quick actions, this class has a mutable subclass, UIMutableApplicationShortcutItem. The following code snippet illustrates one way to use the mutableCopy() method, along with mutable quick actions, to change the title of a dynamic Home Screen quick action:

- Swift
- Objective-C

```
var shortcutItems = UIApplication.shared.shortcutItems ?? []
if let existingShortcutItem = shortcutItems.first {
    guard let mutableShortcutItem = existingShortcutItem.mutableCopy() as? UIMutableApplicationShortcutItem
        else { preconditionFailure("Expected a UIMutableApplicationShortcutItem") }
    guard let index = shortcutItems.index(of: existingShortcutItem)
        else { preconditionFailure("Expected a valid index") }

    mutableShortcutItem.localizedTitle = "New Title"
    shortcutItems[index] = mutableShortcutItem
    UIApplication.shared.shortcutItems = shortcutItems
}
```

```
    NSArray  *existingShortcutItems = [[UIApplication sharedApplication] shortcutItems];
    UIApplicationShortcutItem *existingShortcutItem = [existingShortcutItems firstObject];
    NSMutableArray  *updatedShortcutItems = [existingShortcutItems mutableCopy];
    UIMutableApplicationShortcutItem *mutableShortcutItem = [existingShortcutItem mutableCopy];
    NSInteger index = [existingShortcutItems indexOfObject:existingShortcutItem];
    [mutableShortcutItem setLocalizedTitle: @"New Title"];
    [updatedShortcutItems replaceObjectAtIndex: index withObject: mutableShortcutItem];
    [[UIApplication sharedApplication] setShortcutItems: updatedShortcutItems];
```

### Dynamic and static quick actions

Although immutable, a UIApplicationShortcutItem instance is considered *dynamic* to distinguish it from a *static* quick action you specify at build time.

- Define Home Screen *dynamic* quick actions using this class. Your code creates dynamic quick actions, and registers them with your app object, at runtime.

- Define Home Screen *static* quick actions in the UIApplicationShortcutItems array in your Xcode project’s `Info.plist` file, as described in the iOS Keys chapter in Information Property List Key Reference. The system registers your static quick actions when your app is installed.

The system limits the number of quick actions displayed when a user presses a Home Screen app icon. Within the limited set of displayed quick action titles, your static quick actions are shown first, starting at the topmost position in the list. If your static items don’t consume the permissible number for display and you’ve also defined dynamic quick actions using this class, then one or more of your dynamic quick actions is displayed.

### App launch and app update considerations for quick actions

When a user chooses one of your Home Screen quick actions, the system launches or resumes your app and UIKit calls the application(_:performActionFor:completionHandler:) method in your app delegate. Be sure to read the description of that method in UIApplicationDelegate for information on how to ensure the method is called only when it should be.

After a user first installs your app and before they first launch it, pressing your Home Screen icon displays only the app’s static quick actions. After first launch, your dynamic quick actions (if you’ve defined any and there’s room in the list to accommodate them) are displayed as well.

If a user installs an update for your app but hasn’t yet launched the update, pressing your Home Screen icon shows the dynamic quick actions for the previously installed version. One way to gracefully handle this scenario is to provide app version information in the `userInfo` dictionary of a quick action.

## Topics

### Creating a Home Screen dynamic quick action

convenience init(type: String, localizedTitle: String)

Creates an immutable Home Screen dynamic quick action with a user-visible title and no icon.

init(type: String, localizedTitle: String, localizedSubtitle: String?, icon: UIApplicationShortcutIcon?, userInfo: [String : any NSSecureCoding]?)

Creates an immutable Home Screen dynamic quick action with user-visible title, icon, and user info dictionary.

### Inspecting a Home Screen dynamic quick action

var localizedTitle: String

The required, user-visible title for the Home Screen dynamic quick action.

var localizedSubtitle: String?

The optional, user-visible subtitle for the Home Screen dynamic quick action.

var type: String

A required, app-specific string that you employ to identify the type of quick action to perform.

var icon: UIApplicationShortcutIcon?

The optional icon for the Home Screen dynamic quick action.

var userInfo: [String : any NSSecureCoding]?

Optional, app-specific information that you can provide for use when your app performs the Home screen quick action.

### Designating the scene to activate

var targetContentIdentifier: Any?

The object that determines which scene handles the quick action.

## Relationships

### Inherits From

- NSObject

### Inherited By

- UIMutableApplicationShortcutItem

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSCopying
- NSMutableCopying
- NSObjectProtocol

## See Also

### Home Screen quick actions

Add Home Screen quick actions

Expose commonly used functionality with static or dynamic 3D Touch Home Screen quick actions.

class UIApplicationShortcutIcon

An image you can optionally associate with a Home Screen quick action to improve its appearance and usability.

class UIMutableApplicationShortcutItem

A mutable Home Screen dynamic quick action, which is an item that specifies a configurable user-initiated action for your app.

