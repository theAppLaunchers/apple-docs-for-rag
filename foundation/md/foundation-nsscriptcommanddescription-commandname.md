

- Foundation
- NSScriptCommandDescription
-  commandName 

Instance Property

# commandName

Returns the name of the command.

Mac Catalyst 13.0+macOS 10.0+

``` source
var commandName: String { get }
```

## Return Value

The command name as it appears in the application’s scriptability information; may be different from what is displayed to the scripter.

## See Also

### Getting Basic Information About the Command

var appleEventClassCode: FourCharCode

Returns the four-character code for the Apple event class of the receiver’s command.

var appleEventCode: FourCharCode

Returns the four-character code for the Apple event ID of the receiver’s command.

var commandClassName: String

Returns the name of the class that will be instantiated to handle the command.

var suiteName: String

Returns the name of the suite that contains the command described by the receiver.

