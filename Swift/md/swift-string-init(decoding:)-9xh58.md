

- Swift
- String
-  init(decoding:) 

Initializer

# init(decoding:)

Creates a string by interpreting the path component’s content as UTF-8 on Unix and UTF-16 on Windows.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+watchOS 8.0+

``` source
init(decoding component: FilePath.Component)
```

## Parameters 

`component`  

The path component to be interpreted as `CInterop.PlatformUnicodeEncoding`.

## Discussion

If the content of the path component isn’t a well-formed Unicode string, this initializer replaces invalid bytes with U+FFFD. This means that, depending on the semantics of the specific file system, conversion to a string and back to a path component might result in a value that’s different from the original path component.

