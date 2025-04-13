

- Swift
- String
-  init(platformString:) 

Initializer

# init(platformString:)

Creates a string by interpreting the null-terminated platform string as UTF-8 on Unix and UTF-16 on Windows.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+watchOS 8.0+

``` source
init(platformString: [CInterop.PlatformChar])
```

## Parameters 

`platformString`  

The null-terminated platform string to be interpreted as `CInterop.PlatformUnicodeEncoding`.

## Discussion

- Note It is a precondition that `platformString` must be null-terminated. The absence of a null byte will trigger a runtime error.

If the content of the platform string isn’t well-formed Unicode, this initializer replaces invalid bytes with U+FFFD. This means that, depending on the semantics of the specific platform, conversion to a string and back might result in a value that’s different from the original platform string.

