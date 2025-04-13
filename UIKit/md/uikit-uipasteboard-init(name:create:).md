

- UIKit
- UIPasteboard
-  init(name:create:) 

Initializer

# init(name:create:)

Returns a pasteboard that you identify by name, optionally creating it if it doesn’t exist.

iOS 3.0+iPadOS 3.0+Mac Catalyst 13.1+visionOS 1.0+

``` source
init?(
    name pasteboardName: UIPasteboard.Name,
    create: Bool
)
```

## Parameters 

`pasteboardName`  

A string or string constant that identifies (or should identify) the pasteboard. To create a pasteboard with a `nil` name, specify a `nil` value for this parameter.

`create`  

A Boolean value that specifies whether to create the pasteboard if it doesn’t already exist. Specify false for system pasteboards or if you want to use an existing app pasteboard.

## Return Value

A pasteboard object you can use to transfer data within an app or between apps that have the same team ID.

## Discussion

Call this method to create custom app pasteboards. (You can also use it to obtain the general pasteboard, but the general class method exists for that purpose.) App pasteboards this method returns aren’t persistent, existing only until the app quits. Starting in iOS 10, persistent, named pasteboards are deprecated. Instead, use a shared container, as described in the overview for the UIPasteboard class.

## See Also

### Getting and removing pasteboards

class var general: UIPasteboard

The systemwide general pasteboard, which you use for general copy-paste operations.

class func withUniqueName() -> UIPasteboard

Returns an app pasteboard that you identify by a unique system-generated name.

class func remove(withName: UIPasteboard.Name)

Invalidates the designated app pasteboard.

