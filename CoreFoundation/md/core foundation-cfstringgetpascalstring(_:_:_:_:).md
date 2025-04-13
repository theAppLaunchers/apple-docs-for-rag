

- Core Foundation
-  CFStringGetPascalString(\_:\_:\_:\_:) 

Function

# CFStringGetPascalString(\_:\_:\_:\_:)

Copies the character contents of a CFString object to a local Pascal string buffer after converting the characters to a requested encoding.

iOSiPadOSMac CatalystmacOStvOSvisionOSwatchOS

``` source
func CFStringGetPascalString(
    _ theString: CFString!,
    _ buffer: StringPtr!,
    _ bufferSize: CFIndex,
    _ encoding: CFStringEncoding
) -> Bool
```

## Parameters 

`theString`  

The string to examine.

`buffer`  

The Pascal string buffer into which to copy the `theString`. The buffer must be at least `bufferSize` bytes in length. On return, contains the converted characters. If there is an error in conversion, the buffer contains only partial results.

`bufferSize`  

The length of the local `buffer` in bytes (accounting for the length byte).

`encoding`  

The string encoding to which the character contents of `theString` should be converted.

## Return Value

`true` if the operation succeeds or `false` if the conversion fails or the provided buffer is too small.

## Discussion

This function is useful when you need your own copy of a CFString object’s character data as a Pascal string. You can also call it as a “backup” operation when a prior call to the CFStringGetPascalStringPtr(_:_:) function fails.

## See Also

### Accessing Characters

func CFStringCreateExternalRepresentation(CFAllocator!, CFString!, CFStringEncoding, UInt8) -> CFData!

Creates an “external representation” of a CFString object, that is, a CFData object.

func CFStringGetBytes(CFString!, CFRange, CFStringEncoding, UInt8, Bool, UnsafeMutablePointer&lt;UInt8>!, CFIndex, UnsafeMutablePointer&lt;CFIndex>!) -> CFIndex

Fetches a range of the characters from a string into a byte buffer after converting the characters to a specified encoding.

func CFStringGetCharacterAtIndex(CFString!, CFIndex) -> UniChar

Returns the Unicode character at a specified location in a string.

func CFStringGetCharacters(CFString!, CFRange, UnsafeMutablePointer&lt;UniChar>!)

Copies a range of the Unicode characters from a string to a user-provided buffer.

func CFStringGetCharactersPtr(CFString!) -> UnsafePointer&lt;UniChar>!

Quickly obtains a pointer to the contents of a string as a buffer of Unicode characters.

func CFStringGetCharacterFromInlineBuffer(UnsafeMutablePointer&lt;CFStringInlineBuffer>!, CFIndex) -> UniChar

Returns the Unicode character at a specific location in an in-line buffer.

func CFStringGetCString(CFString!, UnsafeMutablePointer&lt;CChar>!, CFIndex, CFStringEncoding) -> Bool

Copies the character contents of a string to a local C string buffer after converting the characters to a given encoding.

func CFStringGetCStringPtr(CFString!, CFStringEncoding) -> UnsafePointer&lt;CChar>!

Quickly obtains a pointer to a C-string buffer containing the characters of a string in a given encoding.

func CFStringGetLength(CFString!) -> CFIndex

Returns the number (in terms of UTF-16 code pairs) of Unicode characters in a string.

func CFStringGetPascalStringPtr(CFString!, CFStringEncoding) -> ConstStringPtr!

Quickly obtains a pointer to a Pascal buffer containing the characters of a string in a given encoding.

func CFStringGetRangeOfComposedCharactersAtIndex(CFString!, CFIndex) -> CFRange

Returns the range of the composed character sequence at a specified index.

func CFStringInitInlineBuffer(CFString!, UnsafeMutablePointer&lt;CFStringInlineBuffer>!, CFRange)

Initializes an in-line buffer to use for efficient access of a CFString object’s characters.

