

- Security
-  SecTaskCopySigningIdentifier(\_:\_:) 

Function

# SecTaskCopySigningIdentifier(\_:\_:)

Returns the value of the code signing identifier.

Mac Catalyst 13.0+macOS 10.0+

``` source
func SecTaskCopySigningIdentifier(
    _ task: SecTask,
    _ error: UnsafeMutablePointer?>?
) -> CFString?
```

## Parameters 

`task`  

The task whose code signing identifier you want.

`error`  

A pointer that the function uses to provide an error object with details if an error occurs. The caller becomes responsible for the object’s memory. Pass `NULL` to ignore the error.

## Return Value

A string representing the code signing identifier for the task, or `NULL` on error. In Objective-C, call the CFRelease function to free this string’s memory when you are done with it.

