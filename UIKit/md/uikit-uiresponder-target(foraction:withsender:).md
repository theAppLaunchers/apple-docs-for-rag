

- UIKit
- UIResponder
-  target(forAction:withSender:) 

Instance Method

# target(forAction:withSender:)

Returns the target object that responds to an action.

iOS 7.0+iPadOS 7.0+Mac Catalyst 13.1+tvOSvisionOS 1.0+

``` source
@MainActor
func target(
    forAction action: Selector,
    withSender sender: Any?
) -> Any?
```

## Parameters 

`action`  

A selector that identifies a method associated with a command.

`sender`  

The object calling this method. For the editing menu commands, this is the shared UIApplication object. Depending on the context, you can query the sender for information to help you determine the target of the command.

## Return Value

The object whose action method is invoked to execute the command.

## Discussion

This method is called whenever an action needs to be invoked by the object. The default implementation calls the canPerformAction(_:withSender:) method to determine whether it can invoke the action. If the object can invoke the action, it returns itself, otherwise it passes the request up the responder chain. Your app should override this method if it wants to override how a target is selected.

## See Also

### Building and validating commands

func buildMenu(with: any UIMenuBuilder)

Asks the receiving responder to add and remove items from a menu system.

func validate(UICommand)

Asks the receiving responder to validate the command.

func canPerformAction(Selector, withSender: Any?) -> Bool

Requests the receiving responder to enable or disable the specified command in the user interface.

