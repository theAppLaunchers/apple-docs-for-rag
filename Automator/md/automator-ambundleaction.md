

- Automator
-  AMBundleAction 

Class

# AMBundleAction

An object that represents an Automator action that’s a loadable bundle.

Mac Catalyst 14.0+macOS 10.4+

``` source
class AMBundleAction
```

## Overview

Automator loads action bundles from standard locations in the file system: `/System/Library/Automator`, `/Library/Automator`, and `~/Library/Automator`.

AMBundleAction objects have several important properties:

- The Bundle object associated with the action’s physical bundle

- The action’s view, which holds its user interface

- A parameters dictionary that reflects the settings in the user interface

When you create a Cocoa Automator Action project in Xcode, the project template includes a custom subclass of AMBundleAction. This custom class uses the name of the project.

You must provide an implementation of run(withInput:), which is declared by the superclass AMAction. If you add any instance variables, you must override the init(definition:fromArchive:) method and the write(to:) method of AMAction to work with them.

## Topics

### Initializing the Action

func awakeFromBundle()

Allows the action object to perform setup tasks requiring the presence of all bundle objects.

### Managing Action Properties

var bundle: Bundle

The action’s bundle object.

var hasView: Bool

A Boolean value that indicates whether the action has a view associated with it.

var view: NSView?

The action’s view object.

var parameters: NSMutableDictionary?

The action’s parameters.

## Relationships

### Inherits From

- AMAction

### Inherited By

- AMAppleScriptAction
- AMShellScriptAction

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSCoding
- NSCopying
- NSObjectProtocol
- NSSecureCoding

## See Also

### Actions

class AMShellScriptAction

An object that represents Automator actions whose runtime behavior is driven by a shell script or by a Perl or Python script.

class AMAction

An abstract class that defines the interface and general characteristics of Automator actions.

