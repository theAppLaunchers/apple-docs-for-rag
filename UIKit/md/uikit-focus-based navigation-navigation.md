

- UIKit
-  Focus-based navigation 

API Collection

# Focus-based navigation

Navigate the interface of your UIKit app using a remote, game controller, or keyboard.

## Topics

### Focus interactions

Navigating an app’s user interface using a keyboard

Navigate between user interface elements using a keyboard and focusable UI elements in iPad apps and apps built with Mac Catalyst.

About focus interactions for Apple TV

Design and implement intuitive control schemes for menus and interactive user interface layouts.

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

### Focus guides

Creating custom navigation interactions

Build nonstandard navigation interactions that move focus to the desired location.

class UIFocusGuide

An object that exposes nonview areas as focusable.

### Focus debugging

Debugging focus issues in your app

Find errors and determine why the next focused item isn’t what you expected.

class UIFocusDebugger

A runtime object for debugging focus-related interactions.

### Animations

class UIFocusAnimationCoordinator

A coordinator of focus-related animations during a focus update.

### Focus effects

class UIFocusEffect

The base class for defining a visual focus effect.

class UIFocusHaloEffect

A visual focus effect that draws a halo around the focus item.

enum Position

Constants that describe positions for drawing the halo focus effect.

## See Also

### User interactions

Touches, presses, and gestures

Encapsulate your app’s event-handling logic in gesture recognizers so that you can reuse that code throughout your app.

Menus and shortcuts

Simplify interactions with your app using menu systems, contextual menus, Home Screen quick actions, and keyboard shortcuts.

Drag and drop

Bring drag and drop to your app by using interaction APIs with your views.

Pointer interactions

Support pointer interactions in your custom controls and views.

Apple Pencil interactions

Handle user interactions like double tap and squeeze on Apple Pencil.

Accessibility for UIKit

Make your UIKit apps accessible to everyone who uses iOS and tvOS.

