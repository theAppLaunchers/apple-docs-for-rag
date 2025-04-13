

- AppKit
-  NSStoryboard 

Class

# NSStoryboard

An encapsulation of the design-time view controller and window controller graph represented in an Interface Builder storyboard resource file.

macOS 10.10+

``` source
class NSStoryboard
```

## Overview

You can use storyboard files to define the view and window controllers for all or part of an app’s user interface. Typically, AppKit creates these objects automatically in response to actions defined within a storyboard file itself, such as the clicking of a button or the choosing of a menu item. However, you can use a storyboard object to directly instantiate the initial view controller from a storyboard file or to instantiate other view or window controllers that you want to present programmatically. In the context of a storyboard file, each contained controller is called a *scene*.

A transition from one scene to another in a storyboard is called a *segue*. This same term, and the same Cocoa APIs, express a containment relationship between two scenes. In macOS, containment (rather than transition) is the more common notion for storyboards. For descriptions of the related APIs, refer to NSStoryboardSegue and NSSeguePerforming.

## Topics

### Creating a Storyboard Object

convenience init(name: NSStoryboard.Name, bundle: Bundle?)

Creates a storyboard based on the named storyboard file in the specified bundle.

class var main: NSStoryboard?

The app’s main storyboard.

typealias Name

The name of the storyboard file.

### Loading the Initial View Controller

func instantiateInitialController() -> Any?

Creates the initial view controller or window controller from a storyboard.

func instantiateInitialController&lt;Controller>(creator: ((NSCoder) -> Controller?)?) -> Controller?

Creates the initial view controller from the storyboard and initializes it using your custom code.

func instantiateInitialController&lt;Controller>(creator: ((NSCoder) -> Controller?)?) -> Controller?

Creates the initial window controller from the storyboard and initializes it using your custom code.

### Instantiating Storyboard Controllers

func instantiateController(withIdentifier: NSStoryboard.SceneIdentifier) -> Any

Instantiates a specified view controller or window controller from a storyboard.

func instantiateController&lt;Controller>(identifier: NSStoryboard.SceneIdentifier, creator: ((NSCoder) -> Controller?)?) -> Controller

Creates the specified view controller from the storyboard and initializes it using your custom initialization code.

func instantiateController&lt;Controller>(identifier: NSStoryboard.SceneIdentifier, creator: ((NSCoder) -> Controller?)?) -> Controller

Creates the specified window controller from the storyboard and initializes it using your custom initialization code.

typealias SceneIdentifier

A string that uniquely identifies a view controller or window controller in your storyboard file.

## Relationships

### Inherits From

- NSObject

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSObjectProtocol

## See Also

### Storyboard

class NSStoryboardSegue

A transition or containment relationship between two scenes in a storyboard.

protocol NSSeguePerforming

A set of methods that support the mediation of a custom segue.

