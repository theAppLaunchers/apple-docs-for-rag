

- Core Foundation
-  CFStringGetBytes(\_:\_:\_:\_:\_:\_:\_:\_:) 

Function

# CFStringGetBytes(\_:\_:\_:\_:\_:\_:\_:\_:)

Fetches a range of the characters from a string into a byte buffer after converting the characters to a specified encoding.

iOSiPadOSMac CatalystmacOStvOSvisionOSwatchOS

``` source
func CFStringGetBytes(
    _ theString: CFString!,
    _ range: CFRange,
    _ encoding: CFStringEncoding,
    _ lossByte: UInt8,
    _ isExternalRepresentation: Bool,
    _ buffer: UnsafeMutablePointer!,
    _ maxBufLen: CFIndex,
    _ usedBufLen: UnsafeMutablePointer!
) -> CFIndex
```

## Parameters 

`theString`  

The string upon which to operate.

`range`  

The range of characters in `theString` to process. The specified range must not exceed the length of the string.

`encoding`  

The string encoding of the characters to copy to the byte buffer. 8, 16, and 32-bit encodings are supported.

`lossByte`  

A character (for example, ‘?’) that should be substituted for characters that cannot be converted to the specified encoding. Pass `0` if you do not want lossy conversion to occur.

`isExternalRepresentation`  

`true` if you want the result to be in an “external representation” format, otherwise `false`. In an “external representation” format, the result may contain a byte order marker (BOM) specifying endianness and this function might have to perform byte swapping.

`buffer`  

The byte buffer into which the converted characters are written. The buffer can be allocated on the heap or stack. Pass `NULL` if you do not want conversion to take place but instead want to know if conversion will succeed (the function result is greater than `0`) and, if so, how many bytes are required (`usedBufLen`).

`maxBufLen`  

The size of `buffer` and the maximum number of bytes that can be written to it.

`usedBufLen`  

On return, the number of converted bytes actually in `buffer`. You may pass `NULL` if you are not interested in this information.

## Return Value

The number of characters converted.

## Discussion

This function is the basic encoding-conversion function for CFString objects. As with the other functions that get the character contents of CFString objects, it allows conversion to a supported 8-bit encoding. Unlike most of those other functions, it also allows “lossy conversion.” The function permits the specification of a “loss byte” in a parameter; if a character cannot be converted this character is substituted and conversion proceeds. (With the other functions, conversion stops at the first error and the operation fails.)

Because this function takes a range and returns the number of characters converted, it can be called repeatedly with a small fixed size buffer and different ranges of the string to do the conversion incrementally.

This function also handles any necessary manipulation of character data in an “external representation” format. This format makes the data portable and persistent (disk-writable); in Unicode it often includes a BOM (byte order marker) that specifies the endianness of the data.

The CFStringCreateExternalRepresentation(_:_:_:_:) function also handles external representations and performs lossy conversions. The complementary function CFStringCreateWithBytes(_:_:_:_:_:) creates a string from the characters in a byte buffer.

## See Also

### Accessing Characters

func CFStringCreateExternalRepresentation(CFAllocator!, CFString!, CFStringEncoding, UInt8) -> CFData!

Creates an “external representation” of a CFString object, that is, a CFData object.

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

func CFStringGetPascalString(CFString!, StringPtr!, CFIndex, CFStringEncoding) -> Bool

Copies the character contents of a CFString object to a local Pascal string buffer after converting the characters to a requested encoding.

func CFStringGetPascalStringPtr(CFString!, CFStringEncoding) -> ConstStringPtr!

Quickly obtains a pointer to a Pascal buffer containing the characters of a string in a given encoding.

func CFStringGetRangeOfComposedCharactersAtIndex(CFString!, CFIndex) -> CFRange

Returns the range of the composed character sequence at a specified index.

func CFStringInitInlineBuffer(CFString!, UnsafeMutablePointer&lt;CFStringInlineBuffer>!, CFRange)

Initializes an in-line buffer to use for efficient access of a CFString object’s characters.

