

- Swift
- UnsafeMutableRawPointer
-  init(\_:) 

Initializer

# init(\_:)

Creates a new raw pointer from an `AutoreleasingUnsafeMutablePointer` instance.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
init?(_ other: AutoreleasingUnsafeMutablePointer?)
```

## Parameters 

`other`  

The pointer to convert. If `other` is `nil`, the result is `nil`.

