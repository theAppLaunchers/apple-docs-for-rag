

- IOBluetooth
-  OBEXHeadersToBytes(\_:) 

Function

# OBEXHeadersToBytes(\_:)

Converts a dictionary of headers to a data pointer, from which you can extract as bytes and pass to the OBEX command/response functions.

macOS

``` source
func OBEXHeadersToBytes(_ dictionaryOfHeaders: CFDictionary!) -> Unmanaged!
```

## Parameters 

`dictionaryOfHeaders`  

Dictionary that you have added headers to with the above OBEXAddXXXHeader functions.

## Return Value

Mutable data ref containing the bytes of all headers.

## Discussion

Returns a CFMutableDataRef containing all the header data found in the dictionary, formatted according to the OBEX/IrMC spec. YOU MUST RELEASE IT when you are finished with it (ie. when the OBEX request is complete). All OBEX-specification defined headers are supported and should be returned to the dictionary. Use the keys defined above to get headers from dictionary. Example usage:

```

   Example usage:

   CFMutableDictionaryRef dictionary;
   CFMutableDataRef       mGetHeadersDataRef;
   uint8_t*                headerDataPtr;
   uint32_t                headerDataLength;

   dictionary = CFDictionaryCreateMutable( kCFAllocatorDefault, 0, &kCFCopyStringDictionaryKeyCallBacks, &kCFTypeDictionaryValueCallBacks );

   // Package up desired headers.

   OBEXAddTypeHeader( CFSTR( "text/x-vCard" ), dictionary );

   mGetHeadersDataRef = OBEXHeadersToBytes( dictionary );

   headerDataPtr = CFDataGetBytePtr( mGetHeadersDataRef );
   headerDataLength = CFDataGetLength( mGetHeadersDataRef );

   // From here I can pass it to any OBEX command, such as OBEXPut...

```

## See Also

### Miscellaneous

func OBEXAddApplicationParameterHeader(UnsafeRawPointer!, UInt32, CFMutableDictionary!) -> OBEXError

Add bytes representing an application parameter to a dictionary of OBEX headers.

func OBEXAddAuthorizationChallengeHeader(UnsafeRawPointer!, UInt32, CFMutableDictionary!) -> OBEXError

Add an authorization challenge header to a dictionary of OBEXheaders.

func OBEXAddAuthorizationResponseHeader(UnsafeRawPointer!, UInt32, CFMutableDictionary!) -> OBEXError

Add an authorization Response header to a dictionary of OBEXheaders.

func OBEXAddBodyHeader(UnsafeRawPointer!, UInt32, Bool, CFMutableDictionary!) -> OBEXError

Add bytes of data to a dictionary of OBEXheaders.

func OBEXAddByteSequenceHeader(UnsafeRawPointer!, UInt32, CFMutableDictionary!) -> OBEXError

Add a byte sequence header to a dictionary of OBEXheaders.

func OBEXAddConnectionIDHeader(UnsafeRawPointer!, UInt32, CFMutableDictionary!) -> OBEXError

Add bytes representing a connection ID to a dictionary of OBEX headers.

func OBEXAddCountHeader(UInt32, CFMutableDictionary!) -> OBEXError

Add a CFStringRef to a dictionary of OBEXheaders.

func OBEXAddDescriptionHeader(CFString!, CFMutableDictionary!) -> OBEXError

Add a CFStringRef to a dictionary of OBEXheaders.

func OBEXAddHTTPHeader(UnsafeRawPointer!, UInt32, CFMutableDictionary!) -> OBEXError

Add bytes of data to a dictionary of OBEXheaders.

func OBEXAddLengthHeader(UInt32, CFMutableDictionary!) -> OBEXError

Add a CFStringRef to a dictionary of OBEXheaders.

func OBEXAddNameHeader(CFString!, CFMutableDictionary!) -> OBEXError

Add a CFStringRef to a dictionary of OBEXheaders.

func OBEXAddObjectClassHeader(UnsafeRawPointer!, UInt32, CFMutableDictionary!) -> OBEXError

Add an object class header to a dictionary of OBEXheaders.

func OBEXAddTargetHeader(UnsafeRawPointer!, UInt32, CFMutableDictionary!) -> OBEXError

Add bytes of data to a dictionary of OBEXheaders.

func OBEXAddTime4ByteHeader(UInt32, CFMutableDictionary!) -> OBEXError

Add a CFStringRef to a dictionary of OBEXheaders.

func OBEXAddTimeISOHeader(UnsafeRawPointer!, UInt32, CFMutableDictionary!) -> OBEXError

Add bytes to a dictionary of OBEXheaders.

