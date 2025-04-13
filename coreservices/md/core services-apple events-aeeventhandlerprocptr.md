

- Core Services
- Apple Events
-  AEEventHandlerProcPtr 

Type Alias

# AEEventHandlerProcPtr

Defines a pointer to a function that handles one or more Apple events. Your Apple event handler function performs any action requested by the Apple event, adds parameters to the reply Apple event if appropriate (possibly including error information), and returns a result code.

Mac Catalyst 13.0+macOS 10.0+

``` source
typealias AEEventHandlerProcPtr = (UnsafePointer?, UnsafeMutablePointer?, SRefCon?) -> OSErr
```

## Parameters 

`theAppleEvent`  

A pointer to the Apple event to handle. See AppleEvent.

`reply`  

A pointer to the default reply Apple event provided by the Apple Event Manager. See AppleEvent. If no reply is expected, `reply` has descriptor type `typeNull`.

`handlerRefcon`  

The reference constant stored in the Apple event dispatch table when you install the handler function for the Apple event. You can store any 32-bit value in the dispatch table and use it any way you want when the handler is called. The reference constant may have a value of `NULL`.

## Return Value

A result code. See Result Codes. Your handler should always return `noErr` if it successfully handled the Apple event. If an error occurs, your handler should return either `errAEEventNotHandled` or some other nonzero result code. For more information, see the Discussion section.

## Discussion

An Apple event handler should extract any parameters and attributes from the Apple event, perform the requested action, and add parameters to the reply Apple event if appropriate. You must provide an Apple event handler for each Apple event your application supports. The `AEProcessAppleEvent(_:)` function calls one of your Apple event handlers when it processes an Apple event.

If an error occurs because your application cannot understand the event, return `errAEEventNotHandled`, so that the Apple Event Manager may be able to find another handler to handle the event. If the error occurs because the event is impossible to handle as specified, return the result code returned by whatever function caused the failure, or whatever other result code is appropriate.

For example, suppose your application receives a `kAEGetData` event that requests the name of the current printer, and your application cannot handle such an event. In this situation, you should return `errAEEventNotHandled` so that another handler available to the Apple Event Manager can have a chance to handle the event. This strategy allows users to take advantage of system capabilities from within your application via system handlers.

If your Apple event handler calls the AEResolve(_:_:_:) function and `AEResolve` calls an object accessor function in the system object accessor dispatch table, your Apple event handler may not recognize the descriptor type of the token returned by the function. In this case, your handler should return the result code `errAEUnknownObjectType`. When your handler returns this result code, the Apple Event Manager attempts to locate a system Apple event handler that can recognize the token.

For additional information on dealing with error conditions, see OSLGetErrDescProcPtr.

To provide a pointer to your event handler callback function, you create a universal procedure pointer (UPP) of type AEEventHandlerUPP, using the function NewAEEventHandlerUPP(_:). You can do so with code like the following:

AEEventHandlerUPP MyEventHandlerUPP;
MyEventHandlerUPP = NewAEEventHandlerUPP (&amp;MyEventHandlerCallback)

You can then pass the UPP `MyEventHandlerUPP` as a parameter to any function that installs or removes a handler, such as AEInstallEventHandler(_:_:_:_:_:). If your application installs the same event handler to handle more than one kind of event (more than one pair of event class and event ID), you can use the same UPP to install the handler multiple times.

If you wish to call your event handler callback function directly, you can use the InvokeAEEventHandlerUPP(_:_:_:_:) function.

After you are finished with an event handler callback function, and have removed it with the AERemoveEventHandler(_:_:_:_:) function, you can dispose of the UPP with the DisposeAEEventHandlerUPP(_:) function. However, don’t dispose of the UPP if any remaining handler uses it or if you plan to install the handler again.

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

typealias OSLGetErrDescProcPtr

Defines a pointer to an error descriptor callback function. Your error descriptor callback function supplies a pointer to an address where the Apple Event Manager can store the current descriptor if an error occurs during a call to the `AEResolve` function.

typealias OSLGetMarkTokenProcPtr

Defines a pointer to a mark token callback function. Your mark token function returns a mark token.

typealias OSLMarkProcPtr

Defines a pointer to an object marking callback function. Your object-marking function marks a specific Apple event object.

