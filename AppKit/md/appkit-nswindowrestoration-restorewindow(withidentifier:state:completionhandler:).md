

- AppKit
- NSWindowRestoration
-  restoreWindow(withIdentifier:state:completionHandler:) 

Type Method

# restoreWindow(withIdentifier:state:completionHandler:)

Asks the class to provide a new window for the specified identifier.

macOS 10.7+

``` source
@MainActor
static func restoreWindow(
    withIdentifier identifier: NSUserInterfaceItemIdentifier,
    state: NSCoder,
    completionHandler: @escaping (NSWindow?, (any Error)?) -> Void
)
```

``` source
@MainActor
static func restoreWindow(
    withIdentifier identifier: NSUserInterfaceItemIdentifier,
    state: NSCoder
) async throws -> NSWindow
```

**Required**

## Parameters 

`identifier`  

The unique interface item identifier string that was previously associated with the window. Use this string to determine which window to create.

`state`  

A coder object containing the window state information. This coder object contains the combined restorable state of the window, which can include the state of the window, its delegate, window controller, and document object. You can use this state to determine which window to create.

`completionHandler`  

A Block object to execute with the results of creating the window. You must execute this block at some point but may do so after the method returns if needed. This block takes the following parameters:

- The window that was created or `nil` if the window could not be created.

- An error object if the window was not recognized or could not be created for whatever reason; otherwise, specify `nil`.

## Discussion

At launch time, the application object uses this method to recreate a window that was preserved during a previous running of your application. Your implementation of this method can use the `identifier` string and the data in the `state` coder object to determine the type of window and associated objects to create. You only need to create the window. You do not need to restore the configuration of the window using the provided state. AppKit does that for you when you execute the completion handler with a valid window.

For windows that your restoration class recognizes, create (or obtain) the window object and execute the completion handler, passing the window to it. If your restoration class does not recognize the window, or recognizes it but cannot recreate it for whatever reason, pass an error object to the completion handler instead.

If you plan to invoke `completionHandler` after this method returns, you must copy the Block object yourself and release it when you are done with it. For example, you can copy the block and submit it to a queue for execution, after which you can release the block.

## See Also

### Related Documentation

Mac App Programming Guide

