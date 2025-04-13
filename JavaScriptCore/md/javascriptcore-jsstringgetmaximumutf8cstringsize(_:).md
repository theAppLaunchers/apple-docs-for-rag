

- JavaScriptCore
-  JSStringGetMaximumUTF8CStringSize(\_:) 

Function

# JSStringGetMaximumUTF8CStringSize(\_:)

Returns the maximum number of bytes a JavaScript string uses when you convert it into a null-terminated UTF-8 string.

iOS 16.0+iPadOS 16.0+Mac Catalyst 13.0+macOS 10.5+tvOS 9.0+visionOS 1.0+

``` source
func JSStringGetMaximumUTF8CStringSize(_ string: JSStringRef!) -> Int
```

## Parameters 

`string`  

The JSStringRef with the maximum converted size (in bytes) you want to know.

## Return Value

The maximum number of bytes that might be necessary to convert `string` into a null-terminated UTF-8 string. The number of bytes that the conversion actually ends up requiring can be less than this, but never more.

## See Also

### Accessing JavaScript String Information

func JSStringGetLength(JSStringRef!) -> Int

Returns the number of Unicode characters in a JavaScript string.

func JSStringGetCharactersPtr(JSStringRef!) -> UnsafePointer&lt;JSChar>!

Returns a pointer to the Unicode character buffer that serves as the backing store for a JavaScript string.

func JSStringGetUTF8CString(JSStringRef!, UnsafeMutablePointer&lt;CChar>!, Int) -> Int

Converts a JavaScript string into a null-terminated UTF-8 string, and copies the result into an external byte buffer.

