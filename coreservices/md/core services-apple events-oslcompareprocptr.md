

- Core Services
- Apple Events
-  OSLCompareProcPtr 

Type Alias

# OSLCompareProcPtr

Defines a pointer to an object comparison callback function. Your object comparison function compares one Apple event object to another or to the data for a descriptor.

Mac Catalyst 13.0+macOS 10.0+

``` source
typealias OSLCompareProcPtr = (DescType, UnsafePointer?, UnsafePointer?, UnsafeMutablePointer?) -> OSErr
```

## Parameters 

`oper`  

A comparison operator that specifies the type of comparison to perform. The available comparison operators are described in Comparison Operator Constants. For related information, see the function CreateCompDescriptor(_:_:_:_:_:). See DescType.

`obj1`  

A pointer to a token describing the first Apple event object to compare. (Token is defined in AEDisposeToken(_:). See AEDesc.

`obj2`  

A pointer to a token or some other descriptor that specifies either an Apple event object or a value to compare to the Apple event object specified by the `obj1` parameter. See AEDesc.

`result`  

A pointer to a Boolean value where your object comparison function stores a value indicating the result of the comparison operation. You store `TRUE` if the values of the `obj1` and `obj2` parameters have the relationship specified by the `comparisonOperator` parameter; otherwise, you store `FALSE`.

## Return Value

A result code. See Result Codes. Your object comparison function should return `noErr` if it successfully compared the objects and `errAEEventNotHandled` if it can’t compare the objects. When the Apple Event Manager gets an error result of `errAEEventNotHandled`, it attempts to use other methods of comparing the specified objects, such as calling an equivalent system object comparison function.

## Discussion

The Apple Event Manager calls your object comparison function when, in the course of resolving an object specifier, the manager needs to compare an Apple event object with another object or with a value in a descriptor.

If you want the Apple Event Manager to help your application resolve object specifiers of key form `formTest` (and if your application doesn’t specify `kAEIDoWhose` as described in Callback Constants for the AEResolve Function), you should provide an object-counting function, as described in OSLCountProcPtr, and an object comparison function.

It is up to your application to interpret the comparison operators it receives. The meaning of comparison operators differs according to the Apple event objects being compared, and not all comparison operators apply to all object classes. The available comparison operators are described in Comparison Operator Constants.

To provide a pointer to your object comparison callback function, you create a universal procedure pointer (UPP) of type OSLCompareUPP, using the function NewOSLCompareUPP(_:). You can do so with code like the following:

OSLCompareObjectsUPP MyCompareObjectsUPP;
MyCompareObjectsUPP = NewOSLCompareObjectsUPP(&amp;MyCompareObjectsCallback)

You can then pass the UPP `MyCompareObjectsUPP` as a parameter to the AESetObjectCallbacks(_:_:_:_:_:_:_:) function or the AEInstallSpecialHandler(_:_:_:) function.

If you wish to call your object comparison callback function directly, you can use the InvokeOSLCompareUPP(_:_:_:_:_:) function.

After you are finished with your object comparison callback function, you can dispose of the UPP with the DisposeOSLCompareUPP(_:) function. However, if you will use the same object comparison function in subsequent calls to the function `AESetObjectCallbacks` or the function `AEInstallSpecialHandler`, you can reuse the same UPP, rather than dispose of it and later create a new UPP.

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

