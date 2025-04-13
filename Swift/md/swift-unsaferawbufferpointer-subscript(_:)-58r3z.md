

- Swift
- UnsafeRawBufferPointer
-  subscript(\_:) 

Instance Subscript

# subscript(\_:)

Accesses the bytes in the specified memory region.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
subscript(bounds: Range) -> UnsafeRawBufferPointer.SubSequence { get }
```

## Parameters 

`bounds`  

The range of byte offsets to access. The upper and lower bounds of the range must be in the range `0...count`.

