

- Foundation
- NSAttributedString
-  prefersRTFD(in:) 

Instance Method

# prefersRTFD(in:)

Returns a Boolean value that indicates whether the specified range of text prefers RTFD formatting.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+tvOS 18.0+visionOS 2.0+watchOS 11.0+

``` source
func prefersRTFD(in range: NSRange) -> Bool
```

## Parameters 

`range`  

The range of text to test.

## Return Value

true if the range of text prefers RTFD formatting, or false if you can use the RTF format instead.

## Discussion

When an attributed string contains attachments, you must save it using the RTFD file format to preserve the attached files.

## See Also

### Getting the supported text-file formats

class var textTypes: [String]

An array of UTI strings that identify the file types that attributed strings support, either directly or through a user-installed filter service.

class var textUnfilteredTypes: [String]

An array of UTI strings that identify the file types that attributed strings support directly.

