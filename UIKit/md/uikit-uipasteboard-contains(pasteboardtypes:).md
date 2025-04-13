

- UIKit
- UIPasteboard
-  contains(pasteboardTypes:) 

Instance Method

# contains(pasteboardTypes:)

Returns whether the pasteboard holds data of the specified representation type.

iOS 3.0+iPadOS 3.0+Mac Catalyst 13.1+visionOS 1.0+

``` source
func contains(pasteboardTypes: [String]) -> Bool
```

## Parameters 

`pasteboardTypes`  

An array of strings. Each string should identify a representation of the pasteboard item that the pasteboard reader can handle. These string are frequently UTIs. See the class description for more information about pasteboard item types.

## Return Value

true if the pasteboard item holds data of the indicated representation type, otherwise false.

## Discussion

This method works on the first item in the pasteboard. If there are other items, it ignores them. You can use this method when enabling or disabling the Paste menu command.

Starting in iOS 10, you can directly check which data types are present on a pasteboard by using the convenience methods described in Checking for data types on a pasteboard.

## See Also

### Determining types of pasteboard items

var types: [String]

The types of the first item on the pasteboard.

func types(forItemSet: IndexSet?) -> [[String]]?

Returns an array of representation types for each specified pasteboard item.

func contains(pasteboardTypes: [String], inItemSet: IndexSet?) -> Bool

Returns whether the specified pasteboard items contain data of the given representation types.

func itemSet(withPasteboardTypes: [String]) -> IndexSet?

Returns an index set identifying pasteboard items having the specified representation types.

