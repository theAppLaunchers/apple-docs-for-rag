

- Core Foundation
-  CFErrorGetCode(\_:) 

Function

# CFErrorGetCode(\_:)

Returns the error code for a given CFError.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.1+macOS 10.5+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func CFErrorGetCode(_ err: CFError!) -> CFIndex
```

## Parameters 

`err`  

The error to examine. If this is not a valid CFError, the behavior is undefined.

## Return Value

The error code of `err`.

## Discussion

Note that this function returns the error code for the specified CFError, not an error return for the current call.

## See Also

### Getting Information About an Error

func CFErrorGetDomain(CFError!) -> CFErrorDomain!

Returns the error domain for a given CFError.

func CFErrorCopyUserInfo(CFError!) -> CFDictionary!

Returns the user info dictionary for a given CFError.

func CFErrorCopyDescription(CFError!) -> CFString!

Returns a human-presentable description for a given error.

func CFErrorCopyFailureReason(CFError!) -> CFString!

Returns a human-presentable failure reason for a given error.

func CFErrorCopyRecoverySuggestion(CFError!) -> CFString!

Returns a human presentable recovery suggestion for a given error.

