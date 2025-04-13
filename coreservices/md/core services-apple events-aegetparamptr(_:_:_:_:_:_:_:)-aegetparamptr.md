

- Core Services
- Apple Events
-  AEGetParamPtr(\_:\_:\_:\_:\_:\_:\_:) 

Function

# AEGetParamPtr(\_:\_:\_:\_:\_:\_:\_:)

Gets a copy of the data for a specified Apple event parameter from an Apple event or an Apple event record.

macOS 10.0+

``` source
func AEGetParamPtr(
    _ theAppleEvent: UnsafePointer!,
    _ theAEKeyword: AEKeyword,
    _ desiredType: DescType,
    _ actualType: UnsafeMutablePointer!,
    _ dataPtr: UnsafeMutableRawPointer!,
    _ maximumSize: Size,
    _ actualSize: UnsafeMutablePointer!
) -> OSErr
```

## Parameters 

`theAppleEvent`  

A pointer to the Apple event to get the parameter data from.

`theAEKeyword`  

The keyword that specifies the desired Apple event parameter. Some keyword constants are described in Keyword Parameter Constants.

`desiredType`  

The desired descriptor type for the copied data. For a list of AppleScript’s predefined descriptor types, see Descriptor Type Constants.

If the descriptor specified by the `theAEKeyword` parameter is not of the desired type, `AEGetParamPtr` attempts to coerce the data to this type. However, if the desired type is `typeWildCard`, no coercion is performed.

On return, you can determine the actual descriptor type by examining the `typeCode` parameter.

`typeCode`  

A pointer to a descriptor type. On return, specifies the descriptor type of the data pointed to by `dataPtr`. The returned type is either the same as the type specified by the `desiredType` parameter or, if the desired type was type wildcard, the true type of the descriptor. Specify `NULL` if you do not care about this return value. For a list of AppleScript’s predefined descriptor types, see Descriptor Type Constants.

`dataPtr`  

A pointer to a buffer, local variable, or other storage location created and disposed of by your application. The size in bytes must be at least as large as the value you pass in the `maximumSize` parameter. On return, contains the parameter data. Specify `NULL` if you do not care about this return value.

`maximumSize`  

The maximum length, in bytes, of the expected Apple event parameter data. The `AEGetParamPtr` function will not return more data than you specify in this parameter.

`actualSize`  

A pointer to a variable of type `Size`. On return, the length, in bytes, of the data for the specified Apple event parameter. If this value is larger than the value you passed in the `maximumSize` parameter, the buffer pointed to by `dataPtr` was not large enough to contain all of the data for the parameter, though `AEGetParamPtr` does not write beyond the end of the buffer. If the buffer was too small, you can resize it and call `AEGetParamPtr` again. Specify `NULL` if you do not care about this return value.

## Return Value

A result code. See Result Codes.

## Discussion

You should use this function only to extract data from value descriptors such as `typeUTF8Text`.

Because this function allows you to specify a desired type, it can result in coercion. When used correctly, this has the positive effect of returning the data in the desired format. However, it can have side effects you may not be expecting, such as the overhead of calls to coercion handlers. See also the Version Notes section below for possible problems with coercion.

To get Apple event parameter data for your application to use directly, call `AEGetParamPtr`. To get a descriptor for an Apple event parameter to pass on to another Apple Event Manager routine, call AEGetParamDesc(_:_:_:_:).

Before calling `AEGetParamPtr`, you can call the AESizeOfParam(_:_:_:_:) function to determine a size for the `dataPtr` buffer. However, unless you specify `typeWildCard` for the `desiredType` parameter, `AEGetParamPtr` may coerce the data, which may cause the size of the data to change.

In some cases, you may get improved efficiency extracting information from an Apple event with the AEGetDescDataRange(_:_:_:_:) function.

### Version-Notes

Thread safe starting in OS X v10.2.

If the actual parameter you are getting with `AEGetParamPtr` is a record, `AEGetParamPtr` will erroneously allow you to get the parameter as any type at all, when it really should allow only `typeAERecord`, `typeAEList`, or `typeWildcard`. For other types, it will place raw record data into the designated buffer. With AppleScript 1.1.2, it would then return `errAECoercionFail`, as expected. With AppleScript 1.3 and later, however, it returns `noErr`.

You can work around this problem by checking the returned parameter from any call to `AEGetParamPtr`. If the source type is `typeAERecord` and the type you asked for was anything other than `typeAERecord`, `typeAEList`, or `typeWildcard`, you should assume the coercion failed.

## See Also

### Getting Data or Descriptors From Apple Events and Apple Event Records

func AEGetAttributeDesc(UnsafePointer&lt;AppleEvent>!, AEKeyword, DescType, UnsafeMutablePointer&lt;AEDesc>!) -> OSErr

Gets a copy of the descriptor for a specified Apple event attribute from an Apple event; typically used when your application needs to pass the descriptor on to another function.

func AEGetAttributePtr(UnsafePointer&lt;AppleEvent>!, AEKeyword, DescType, UnsafeMutablePointer&lt;DescType>!, UnsafeMutableRawPointer!, Size, UnsafeMutablePointer&lt;Size>!) -> OSErr

Gets a copy of the data for a specified Apple event attribute from an Apple event; typically used when your application needs to work with the data directly.

func AEGetParamDesc(UnsafePointer&lt;AppleEvent>!, AEKeyword, DescType, UnsafeMutablePointer&lt;AEDesc>!) -> OSErr

Gets a copy of the descriptor for a keyword-specified Apple event parameter from an Apple event or an Apple event record.

