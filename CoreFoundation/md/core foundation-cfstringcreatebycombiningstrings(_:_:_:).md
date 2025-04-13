

- Core Foundation
-  CFStringCreateByCombiningStrings(\_:\_:\_:) 

Function

# CFStringCreateByCombiningStrings(\_:\_:\_:)

Creates a single string from the individual CFString objects that comprise the elements of an array.

iOSiPadOSMac CatalystmacOStvOSvisionOSwatchOS

``` source
func CFStringCreateByCombiningStrings(
    _ alloc: CFAllocator!,
    _ theArray: CFArray!,
    _ separatorString: CFString!
) -> CFString!
```

## Parameters 

`alloc`  

The allocator to use to allocate memory for the new string. Pass `NULL` or kCFAllocatorDefault to use the current default allocator.

`theArray`  

An array of CFString objects to concatenate. This value should not be `NULL`.

`separatorString`  

The string to insert between the substrings in the returned string. This value is commonly a whitespace character such as a tab or a newline (carriage return). If this value is not a valid CFString object, an assertion is raised.

## Return Value

A string that contains a concatenation of the strings in `theArray` separated by `separatorString`. The order of the substrings in the string is identical to the order of the elements in `theArray`.

## Discussion

If `theArray` is empty, returns an empty CFString object; if `theArray` contains one CFString object, that object is returned (without the separator string). Returns `NULL` if there was a problem in creating the string. Ownership follows the The Create Rule.

## Discussion

See also CFStringCreateArrayBySeparatingStrings(_:_:_:).

## See Also

### Creating a CFString

func CFStringCreateArrayBySeparatingStrings(CFAllocator!, CFString!, CFString!) -> CFArray!

Creates an array of CFString objects from a single CFString object.

func CFStringCreateCopy(CFAllocator!, CFString!) -> CFString!

Creates an immutable copy of a string.

func CFStringCreateFromExternalRepresentation(CFAllocator!, CFData!, CFStringEncoding) -> CFString!

Creates a string from its “external representation.”

func CFStringCreateWithBytes(CFAllocator!, UnsafePointer&lt;UInt8>!, CFIndex, CFStringEncoding, Bool) -> CFString!

Creates a string from a buffer containing characters in a specified encoding.

func CFStringCreateWithBytesNoCopy(CFAllocator!, UnsafePointer&lt;UInt8>!, CFIndex, CFStringEncoding, Bool, CFAllocator!) -> CFString!

Creates a string from a buffer, containing characters in a specified encoding, that might serve as the backing store for the new string.

func CFStringCreateWithCharacters(CFAllocator!, UnsafePointer&lt;UniChar>!, CFIndex) -> CFString!

Creates a string from a buffer of Unicode characters.

func CFStringCreateWithCharactersNoCopy(CFAllocator!, UnsafePointer&lt;UniChar>!, CFIndex, CFAllocator!) -> CFString!

Creates a string from a buffer of Unicode characters that might serve as the backing store for the object.

func CFStringCreateWithCString(CFAllocator!, UnsafePointer&lt;CChar>!, CFStringEncoding) -> CFString!

Creates an immutable string from a C string.

func CFStringCreateWithCStringNoCopy(CFAllocator!, UnsafePointer&lt;CChar>!, CFStringEncoding, CFAllocator!) -> CFString!

Creates a CFString object from an external C string buffer that might serve as the backing store for the object.

func CFStringCreateWithFormatAndArguments(CFAllocator!, CFDictionary!, CFString!, CVaListPointer) -> CFString!

Creates an immutable string from a formatted string and a variable number of arguments (specified in a parameter of type `va_list`).

func CFStringCreateWithPascalString(CFAllocator!, ConstStr255Param!, CFStringEncoding) -> CFString!

Creates an immutable CFString object from a Pascal string.

func CFStringCreateWithPascalStringNoCopy(CFAllocator!, ConstStr255Param!, CFStringEncoding, CFAllocator!) -> CFString!

Creates a CFString object from an external Pascal string buffer that might serve as the backing store for the object.

func CFStringCreateWithSubstring(CFAllocator!, CFString!, CFRange) -> CFString!

Creates an immutable string from a segment (substring) of an existing string.

