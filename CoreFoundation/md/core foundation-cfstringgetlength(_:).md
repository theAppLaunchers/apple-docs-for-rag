

- Core Foundation
-  CFStringGetLength(\_:) 

Function

# CFStringGetLength(\_:)

Returns the number (in terms of UTF-16 code pairs) of Unicode characters in a string.

iOSiPadOSMac CatalystmacOStvOSvisionOSwatchOS

``` source
func CFStringGetLength(_ theString: CFString!) -> CFIndex
```

## Parameters 

`theString`  

The string to examine.

## Return Value

The number (in terms of UTF-16 code pairs) of characters stored in `theString`.

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

func CFStringGetPascalString(CFString!, StringPtr!, CFIndex, CFStringEncoding) -> Bool

Copies the character contents of a CFString object to a local Pascal string buffer after converting the characters to a requested encoding.

func CFStringGetPascalStringPtr(CFString!, CFStringEncoding) -> ConstStringPtr!

Quickly obtains a pointer to a Pascal buffer containing the characters of a string in a given encoding.

func CFStringGetRangeOfComposedCharactersAtIndex(CFString!, CFIndex) -> CFRange

Returns the range of the composed character sequence at a specified index.

func CFStringInitInlineBuffer(CFString!, UnsafeMutablePointer&lt;CFStringInlineBuffer>!, CFRange)

Initializes an in-line buffer to use for efficient access of a CFString object’s characters.

