

- Core Services
- Apple Events
-  OSLGetErrDescProcPtr 

Type Alias

# OSLGetErrDescProcPtr

Defines a pointer to an error descriptor callback function. Your error descriptor callback function supplies a pointer to an address where the Apple Event Manager can store the current descriptor if an error occurs during a call to the `AEResolve` function.

Mac Catalyst 13.0+macOS 10.0+

``` source
typealias OSLGetErrDescProcPtr = (UnsafeMutablePointer?>?) -> OSErr
```

## Parameters 

`appDescPtr`  

A pointer to a pointer to a descriptor address. Your error descriptor callback function supplies a pointer to an address of a descriptor where the Apple Event Manager can store the current descriptor if an error occurs. See AEDesc.

## Return Value

A result code. See Result Codes. Your error descriptor function should return `noErr` if it completes successfully and a nonzero error value if it is unsuccessful. If it returns a nonzero value, the Apple Event Manager continues to resolve the object specifier as if it had never called the error callback function.

## Discussion

Your get error descriptor callback function simply supplies a pointer to an address. Shortly after your application calls the AEResolve(_:_:_:) function, the Apple Event Manager calls your get error descriptor callback function and writes a null descriptor to the address supplied by your callback, overwriting whatever was there previously.

If an error occurs during the resolution of the object specifier, the Apple Event Manager calls your get error descriptor callback function again and writes the descriptor it is currently working with—often an object specifier—to the address supplied by your callback. If `AEResolve` returns an error during the resolution of an object specifier, this address contains the descriptor responsible for the error.

You should always write a null descriptor at the address provided by your get error descriptor callback function before calling `AEResolve`. When recovering from an error, the Apple Event Manager, never writes to the address you provide unless it already contains a null descriptor. You may wish to maintain a single global variable of type `AEDesc` and have your get error descriptor callback function always provide the address of that variable.

After `AEResolve` returns, if your error descriptor is not the null descriptor, you are responsible for disposing of it.

To provide a pointer to your get error descriptor callback function, you create a universal procedure pointer (UPP) of type OSLGetErrDescUPP, using the function NewOSLGetErrDescUPP(_:). You can do so with code like the following:

OSLGetErrorDescUPP MyGetErrorDescUPP;
MyGetErrorDescUPP = NewOSLGetErrorDescUPP (&amp;MyGetErrorDescCallback)

You can then pass the UPP `MyGetErrorDescUPP` as a parameter to the AESetObjectCallbacks(_:_:_:_:_:_:_:) function or the AEInstallSpecialHandler(_:_:_:) function.

If you wish to call your get error descriptor callback function directly, you can use the InvokeOSLGetErrDescUPP(_:_:) function.

After you are finished with your get error descriptor callback function, you can dispose of the UPP with the DisposeOSLGetErrDescUPP(_:) function. However, if you will use the same get error descriptor callback function in subsequent calls to the function `AESetObjectCallbacks` or the function `AEInstallSpecialHandler`, you can reuse the same UPP, rather than dispose of it and later create a new UPP.

## See Also

### Callbacks

typealias AERemoteProcessResolverCallback

Defines a pointer to a function the Apple Event Manager calls when the asynchronous execution of a remote process resolver completes, either due to success or failure, after a call to the `AERemoteProcessResolverScheduleWithRunLoop` function. Your callback function can use the reference passed to it to get the remote process information.

typealias AEDisposeExternalProcPtr

Defines a pointer to a function the Apple Event Manager calls to dispose of a descriptor created by the `AECreateDescFromExternalPtr` function. Your callback function disposes of the buffer you originally passed to that function.

typealias AECoerceDescProcPtr

Defines a pointer to a function that coerces data stored in a descriptor. Your descriptor coercion callback function coerces the data from the passed descriptor to the specified type, returning the coerced data in a second descriptor.

typealias AECoercePtrProcPtr

Defines a pointer to a function that coerces data stored in a buffer. Your pointer coercion callback routine coerces the data from the passed buffer to the specified type, returning the coerced data in a descriptor.

typealias AEEventHandlerProcPtr

Defines a pointer to a function that handles one or more Apple events. Your Apple event handler function performs any action requested by the Apple event, adds parameters to the reply Apple event if appropriate (possibly including error information), and returns a result code.

typealias OSLAccessorProcPtr

Your object accessor function either finds elements or properties of an Apple event object.

typealias OSLAdjustMarksProcPtr

Defines a pointer to an adjust marks callback function. Your adjust marks function unmarks objects previously marked by a call to your marking function.

typealias OSLCompareProcPtr

Defines a pointer to an object comparison callback function. Your object comparison function compares one Apple event object to another or to the data for a descriptor.

typealias OSLCountProcPtr

Defines a pointer to an object counting callback function. Your object counting function counts the number of Apple event objects of a specified class in a specified container object.

typealias OSLDisposeTokenProcPtr

Defines a pointer to a dispose token callback function. Your dispose token function, required only if you use a complex token format, disposes of the specified token.

typealias OSLGetMarkTokenProcPtr

Defines a pointer to a mark token callback function. Your mark token function returns a mark token.

typealias OSLMarkProcPtr

Defines a pointer to an object marking callback function. Your object-marking function marks a specific Apple event object.

