

- AppKit
- NSApplication
-  target(forAction:to:from:) 

Instance Method

# target(forAction:to:from:)

Searches for an object that can receive the message specified by the given selector.

macOS

``` source
@MainActor
func target(
    forAction action: Selector,
    to target: Any?,
    from sender: Any?
) -> Any?
```

## Parameters 

`action`  

The desired action message. May be `nil`, in which case this method will return `nil`.

`target`  

The target object to check. Specify `nil` if you want to search the responder chain starting with the current first responder.

`sender`  

The potential sender for the action message.

## Return Value

The object that can accept the specified action message or `nil` if no target object can receive the message from the specified `sender`. Returns `nil` if `anAction` is `nil`.

## Discussion

The system looks for an object that implements a method matching `anAction`.

If `aTarget` is specified, the system verifies that it’s a valid target for the provided action and sender, returning `aTarget` if valid, `nil` otherwise.

If the provided target is `nil`, the search begins with the first responder of the key window. The system follows the responder object looking for targets. If no object capable of handling the message is found in the responder chain, the system returns `nil`.

## See Also

### Posting Actions

func tryToPerform(Selector, with: Any?) -> Bool

Dispatches an action message to the specified target.

func sendAction(Selector, to: Any?, from: Any?) -> Bool

Sends the given action message to the given target.

func target(forAction: Selector) -> Any?

Returns the object that receives the action message specified by the given selector.

