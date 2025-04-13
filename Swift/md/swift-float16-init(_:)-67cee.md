

- Swift
- Float16
-  init(\_:) 

Initializer

# init(\_:)

Creates a new value, rounded to the closest possible representation.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+macOS 11.0+tvOS 14.0+visionOS 1.0+watchOS 7.0+

``` source
init(_ value: Source) where Source : BinaryInteger
```

## Parameters 

`value`  

The integer to convert to a floating-point value.

## Discussion

If two representable values are equally close, the result is the value with more trailing zeros in its significand bit pattern.

