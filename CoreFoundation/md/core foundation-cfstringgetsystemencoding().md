

- Core Foundation
-  CFStringGetSystemEncoding() 

Function

# CFStringGetSystemEncoding()

Returns the default encoding used by the operating system when it creates strings.

iOSiPadOSMac CatalystmacOStvOSvisionOSwatchOS

``` source
func CFStringGetSystemEncoding() -> CFStringEncoding
```

## Return Value

The default string encoding.

## Discussion

This function returns the default text encoding used by the OS when it creates strings. In macOS, this encoding is determined by the user’s preferred language setting. The preferred language is the first language listed in the International pane of the System Preferences.

In most situations you will not want to use this function, however, because your primary interest will be your application’s default text encoding. The application encoding is required when you create a CFStringRef from strings stored in Resource Manager resources, which typically use one of the Mac encodings such as MacRoman or MacJapanese.

To get your application’s default text encoding, call the `GetApplicationTextEncoding` Carbon function.

## See Also

### Working With Encodings

func CFStringConvertEncodingToIANACharSetName(CFStringEncoding) -> CFString!

Returns the name of the IANA registry “charset” that is the closest mapping to a specified string encoding.

func CFStringConvertEncodingToNSStringEncoding(CFStringEncoding) -> UInt

Returns the Cocoa encoding constant that maps most closely to a given Core Foundation encoding constant.

func CFStringConvertEncodingToWindowsCodepage(CFStringEncoding) -> UInt32

Returns the Windows codepage identifier that maps most closely to a given Core Foundation encoding constant.

func CFStringConvertIANACharSetNameToEncoding(CFString!) -> CFStringEncoding

Returns the Core Foundation encoding constant that is the closest mapping to a given IANA registry “charset” name.

func CFStringConvertNSStringEncodingToEncoding(UInt) -> CFStringEncoding

Returns the Core Foundation encoding constant that is the closest mapping to a given Cocoa encoding.

func CFStringConvertWindowsCodepageToEncoding(UInt32) -> CFStringEncoding

Returns the Core Foundation encoding constant that is the closest mapping to a given Windows codepage identifier.

func CFStringGetFastestEncoding(CFString!) -> CFStringEncoding

Returns for a CFString object the character encoding that requires the least conversion time.

func CFStringGetListOfAvailableEncodings() -> UnsafePointer&lt;CFStringEncoding>!

Returns a pointer to a list of string encodings supported by the current system.

func CFStringGetMaximumSizeForEncoding(CFIndex, CFStringEncoding) -> CFIndex

Returns the maximum number of bytes a string of a specified length (in Unicode characters) will take up if encoded in a specified encoding.

func CFStringGetMostCompatibleMacStringEncoding(CFStringEncoding) -> CFStringEncoding

Returns the most compatible Mac OS script value for the given input encoding.

func CFStringGetNameOfEncoding(CFStringEncoding) -> CFString!

Returns the canonical name of a specified string encoding.

func CFStringGetSmallestEncoding(CFString!) -> CFStringEncoding

Returns the smallest encoding on the current system for the character contents of a string.

func CFStringIsEncodingAvailable(CFStringEncoding) -> Bool

Determines whether a given Core Foundation string encoding is available on the current system.

