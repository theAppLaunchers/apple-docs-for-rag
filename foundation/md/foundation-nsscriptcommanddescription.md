

- Foundation
-  NSScriptCommandDescription 

Class

# NSScriptCommandDescription

A script command that a macOS app supports.

Mac Catalyst 13.0+macOS 10.0+

``` source
class NSScriptCommandDescription
```

## Overview

A scriptable application provides scriptability information that describes the commands and objects scripters can use in scripts that target the application. An application’s scripting information is collected automatically by an instance of NSScriptSuiteRegistry, which creates an `NSScriptCommandDescription` for each command it finds, caches these objects in memory, and installs a command handler for each command.

A script command instance stores the name, class, argument types, and return type of a command. For example, commands in AppleScript’s Core suite include `clone`, `count`, `create`, `delete`, `exists`, and `move`.

The public methods of `NSScriptCommandDescription` are used primarily by Cocoa’s built-in scripting support in responding to Apple events that target the application. Although you can subclass the `NSScriptCommandDescription` class, it is unlikely that you would need to do so, or to create instances of it.

## Topics

### Initializing a Script Command Description

init?(suiteName: String, commandName: String, dictionary: [AnyHashable : Any]?)

Initializes and returns a newly allocated instance of `NSScriptCommandDescription`.

### Getting Basic Information About the Command

var appleEventClassCode: FourCharCode

Returns the four-character code for the Apple event class of the receiver’s command.

var appleEventCode: FourCharCode

Returns the four-character code for the Apple event ID of the receiver’s command.

var commandClassName: String

Returns the name of the class that will be instantiated to handle the command.

var commandName: String

Returns the name of the command.

var suiteName: String

Returns the name of the suite that contains the command described by the receiver.

### Getting Command Argument Information

func appleEventCodeForArgument(withName: String) -> FourCharCode

Returns the Apple event code for the specified command argument of the receiver.

var argumentNames: [String]

Returns the names (or keys) for all arguments of the receiver’s command.

func isOptionalArgument(withName: String) -> Bool

Returns a Boolean value that indicates whether the command argument identified by the specified argument key is an optional argument.

func typeForArgument(withName: String) -> String?

Returns the type of the command argument identified by the specified key.

### Getting Command Return-Type Information

var appleEventCodeForReturnType: FourCharCode

Returns the Apple event code that identifies the command’s return type.

var returnType: String?

Returns the return type of the command.

### Creating Commands

func createCommandInstance() -> NSScriptCommand

Creates and returns an instance of the command object described by the receiver.

func createCommandInstance(with: NSZone?) -> NSScriptCommand

Creates and returns an instance of the command object described by the receiver in the specified memory zone.

### Initializers

init?(coder: NSCoder)

## Relationships

### Inherits From

- NSObject

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSCoding
- NSObjectProtocol

## See Also

### Script Dictionary Description

class NSScriptSuiteRegistry

The top-level repository of scriptability information for an app at runtime.

class NSScriptClassDescription

A scriptable class that a macOS app supports.

class NSClassDescription

An abstract class that provides the interface for querying the relationships and properties of a class.

