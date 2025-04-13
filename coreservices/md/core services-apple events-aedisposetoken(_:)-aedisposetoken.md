

- Core Services
- Apple Events
-  AEDisposeToken(\_:) 

Function

# AEDisposeToken(\_:)

Deallocates the memory used by a token.

macOS 10.0+

``` source
func AEDisposeToken(_ theToken: UnsafeMutablePointer!) -> OSErr
```

## Parameters 

`theToken`  

A pointer to the token to dispose of. On successful return, the pointer is set to the null descriptor. See AEDesc.

## Return Value

A result code. See Result Codes.

## Discussion

Your application calls the AEResolve(_:_:_:) function to resolve an object specifier, with the help of the object accessor functions described in “Object Accessor Callbacks” and the application object callback functions described in “Object Callback Functions”.

When `AEResolve` returns a final token to your event handler as the result of the resolution of an object specifier, your application must deallocate the memory used by the token. When your application calls the `AEDisposeToken` function, the Apple Event Manager first calls your application’s token disposal function, if you have provided one. The token disposal function is described in OSLDisposeTokenProcPtr.

If you haven’t provided a token disposal function, or if your application’s token disposal function returns `errAEEventNotHandled` as the function result, the Apple Event Manager calls the system token disposal function if one is available. If there is no system token disposal function or the function returns `errAEEventNotHandled` as the function result, the Apple Event Manager calls the `AEDisposeDesc` function to dispose of the token.

### Version-Notes

In macOS, your application can not make an object callback function available to other applications by installing it in a system object accessor dispatch table.

