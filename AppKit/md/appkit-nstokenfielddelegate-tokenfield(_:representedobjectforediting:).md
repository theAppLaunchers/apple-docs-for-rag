

- AppKit
- NSTokenFieldDelegate
-  tokenField(\_:representedObjectForEditing:) 

Instance Method

# tokenField(\_:representedObjectForEditing:)

Allows the delegate to provide a represented object for the given editing string.

macOS

``` source
@MainActor
optional func tokenField(
    _ tokenField: NSTokenField,
    representedObjectForEditing editingString: String
) -> Any?
```

## Parameters 

`tokenField`  

The token field that sent the message.

`editingString`  

The edited string representation of a represented object.

## Return Value

A represented object that is displayed rather than the editing string.

## Discussion

If your application uses some object other than an `NSString` for their represented objects, you should return a new, autoreleased instance of that object from this method.

Note

In OS X v10.4, `NSTokenField` trims whitespace around tokens but it does not trim whitespace in macOS versions 10.5.0 and 10.5.1. In OS X v10.5.2, you get whitespace-trimming behavior by either linking against the v10.4 binary or linking against the v10.5 binary and *not* implementing the this method. If you do not want the whitespace-trimming behavior, link against the v10.5 binary and implement this method, returning the editing string if you have no represented object.

## See Also

### Editing a Tokenized Strings

func tokenField(NSTokenField, completionsForSubstring: String, indexOfToken: Int, indexOfSelectedItem: UnsafeMutablePointer&lt;Int>?) -> [Any]?

Allows the delegate to provide an array of appropriate completions for the contents of the receiver.

func tokenField(NSTokenField, editingStringForRepresentedObject: Any) -> String?

Allows the delegate to provide a string to be edited as a proxy for a represented object.

func tokenField(NSTokenField, shouldAdd: [Any], at: Int) -> [Any]

Allows the delegate to validate the tokens to be added to the receiver at a particular location.

