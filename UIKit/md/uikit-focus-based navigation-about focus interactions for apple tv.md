

- UIKit
- Focus-based navigation
-  About focus interactions for Apple TV 

Article

# About focus interactions for Apple TV

Design and implement intuitive control schemes for menus and interactive user interface layouts.

## Overview

On iOS devices, a user interacts directly with the touchscreen. On Apple TV, a remote or other input device is used to control the interface indirectly. Focus refers to the effect onscreen of external, indirect user input from an input device. As the user navigates through the interface, the next focusable item in the direction in which the user is navigating becomes focused, which triggers a focus update. If the focused item is selectable, the user selects it with the remote. Certain items, such as tab bars, are automatically selected after a slight delay.

The UIKit framework supports focus-based interfaces only, and in most cases this behavior is automatically provided. For apps with custom user interface components, you need to implement custom focus behavior.

### Understanding the focus engine

The system within UIKit that controls focus and focus movement is called the focus engine. The focus engine listens for incoming focus-movement events in your app. When an event comes in, the focus engine automatically determines the next focusable item and notifies your app. This creates a consistent user experience across apps, provides automatic support for all current and future input methods, and helps developers concentrate on implementing their app’s unique behavior rather than defining or reinventing basic navigation.

Only the focus engine can explicitly update focus, meaning there’s no API for directly setting the focused item or moving focus in a particular direction. The focus engine updates focus only when the user sends a movement event or when the system or the app requests an update. Keep the following focus behaviors in mind when creating your layout design:

**Not all items are focusable.** If an item isn’t focusable, it’s ignored whenever focus is determined. Use the canBecomeFocused property to determine if an item is focusable.

**Only a single item can have focus at any given time.**

**Users change focus by selecting a direction on the remote.** UIKit then attempts to move the focus to a new user interface element in that direction. If the system finds another item that can accept focus in that direction, the found item gains focus. If no element is found in that direction, the currently focused item stays in focus and a movementDidFailNotification notification is broadcast.

**Only the user can directionally change focus.** Your app can’t programmatically search for a new element in a given direction. Although you can change focus programmatically, there are restrictions on how focus may change. Focus should almost always be under user control. For example, if the contents of a table view changed and the original focus element no longer exists, it’s reasonable to have your app programmatically select a new item to be in focus.

**Focus is managed by the focus environment.** When a focus environment gains focus, it can either keep the focus or give that focus to one of its own child focus environments. The focus environment it selects is its preferred focus environment. If a child focus environment is chosen, the child focus environment can also choose whether to keep focus or pass it to one of its child focus environments. This process drills down until a focus environment accepts focus for itself. The root view controller of the window also participates in the focus process. The root view controller’s preferredFocusEnvironments property is the first focus environment that’s selected to gain focus.

## See Also

### Focus interactions

Navigating an app’s user interface using a keyboard

Navigate between user interface elements using a keyboard and focusable UI elements in iPad apps and apps built with Mac Catalyst.

Adding user-focusable elements to a tvOS app

Create intuitive and easily manipulated user-interactive controls for your tvOS app.

protocol UIFocusEnvironment

A set of methods that define the focus behavior for a branch of the view hierarchy.

class UIFocusSystem

Queries and reevaluates the currently focused item.

class UIFocusUpdateContext

An object that provides information relevant to a specific focus update from one view to another.

protocol UIFocusItem

An object that can become focused.

class UIFocusMovementHint

Provides movement hint information for the focused item.

protocol UIFocusItemContainer

The container responsible for providing geometric context to focus items within a given focus environment.

protocol UIFocusItemScrollableContainer

A type of focus item container that supports automatic scrolling of focusable content.

struct UIFocusGroupPriority

The importance of an item within a focus group, used by the focus system to determine the group’s primary item.

