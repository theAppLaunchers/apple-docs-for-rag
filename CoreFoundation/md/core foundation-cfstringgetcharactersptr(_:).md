

- Core Foundation
-  CFStringGetCharactersPtr(\_:) 

Function

# CFStringGetCharactersPtr(\_:)

Quickly obtains a pointer to the contents of a string as a buffer of Unicode characters.

iOSiPadOSMac CatalystmacOStvOSvisionOSwatchOS

``` source
func CFStringGetCharactersPtr(_ theString: CFString!) -> UnsafePointer!
```

## Parameters 

`theString`  

The string whose contents you wish to access.

## Return Value

A pointer to a buffer of Unicode character, or `NULL` if the internal storage of `theString` does not allow this to be returned efficiently.

## Discussion

This function either returns the requested pointer immediately, with no memory allocations and no copying, or it returns `NULL`. If the latter is the result, call an alternative function such as CFStringGetCharacters(_:_:_:) function to extract the characters.

Whether or not this function returns a valid pointer or `NULL` depends on many factors, all of which depend on how the string was created and its properties. In addition, the function result might change between different releases and on different platforms. So do not count on receiving a non-`NULL` result from this function under any circumstances (except when the object is created with CFStringCreateMutableWithExternalCharactersNoCopy(_:_:_:_:_:)).

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

