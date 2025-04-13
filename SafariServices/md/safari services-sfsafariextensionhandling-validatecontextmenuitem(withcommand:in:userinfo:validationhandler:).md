

- Safari Services
- SFSafariExtensionHandling
-  validateContextMenuItem(withCommand:in:userInfo:validationHandler:) 

Instance Method

# validateContextMenuItem(withCommand:in:userInfo:validationHandler:)

Validates whether a particular contextual menu item should be displayed.

macOS 10.12.4+

``` source
optional func validateContextMenuItem(
    withCommand command: String,
    in page: SFSafariPage,
    userInfo: [String : Any]? = nil,
    validationHandler: @escaping (Bool, String?) -> Void
)
```

## Parameters 

`command`  

The command, specified in the `Info.plist` file, for the context menu item being validated.

`page`  

The page where the context menu item is going to be presented.

`userInfo`  

Optional message content. If specified, the dictionary’s value objects conform to the W3C standard for safe passing of structured data, such as Boolean objects, numeric values, strings, and arrays.

`validationHandler`  

A code block used to set the state of the contextual menu item. The block receives the following parameters:

shouldHide  
A Boolean value that indicates whether the menu item should be hidden.

text  
The text to use for the menu item. Pass `nil` to use the default text from the `Info.plist` file.

## Mentioned in 

Adjusting settings for contextual menu items

## Discussion

If you do not implement this method, the contextual menu item is always available. Otherwise, this method is called before the contextual menu is shown so that you can determine whether the menu item should be displayed and the text that appears in the item.

Important

This method is called by Safari after the user has already clicked to display the menu and before the menu is displayed. Because this is a time-sensitive operation, your extension should call the validation handler as soon as possible after receiving the call. If an extension does not respond in a reasonable period of time, Safari will display the contextual menu item using the default text.

To hide the contextual menu item:

- Swift
- Objective-C

```
validationHandler(true, nil)
```

```
validationHandler(YES, nil);
```

To change the menu text:

- Swift
- Objective-C

```
validationHandler(false, "Updated text")
```

```
validationHandler(NO, @"Updated text");
```

To use the default text:

- Swift
- Objective-C

```
validationHandler(false, nil)
```

```
validationHandler(NO, nil)
```

## See Also

### Responding to Context Menu Selections

func contextMenuItemSelected(withCommand: String, in: SFSafariPage, userInfo: [String : Any]?)

A method the system calls when a user selects one of the app extension’s context menu items.

