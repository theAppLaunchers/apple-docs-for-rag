

- Foundation
- NSScriptClassDescription
-  selector(forCommand:) 

Instance Method

# selector(forCommand:)

Returns the selector associated with the receiver for the specified command description.

Mac Catalyst 13.0+macOS 10.0+

``` source
func selector(forCommand commandDescription: NSScriptCommandDescription) -> Selector?
```

## Parameters 

`commandDescription`  

A description for a script command, such as `duplicate`, `make`, or `move`. Encapsulates the scriptability information for that command, such as its Objective-C selector, its argument names and types, and its return type (if any).

## Return Value

The selector from the receiver for the command specified by `commandDescription`. Searches in the receiver first, then in any superclass. Returns `NULL` if no matching selector is found.

## See Also

### Getting command information

func supportsCommand(NSScriptCommandDescription) -> Bool

Returns a Boolean value indicating whether the receiver or any superclass supports the specified command.

