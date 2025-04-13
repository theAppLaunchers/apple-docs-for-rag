

- Swift
-  numericCast(\_:) 

Function

# numericCast(\_:)

Returns the given integer as the equivalent value in a different integer type.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func numericCast(_ x: T) -> U where T : BinaryInteger, U : BinaryInteger
```

## Parameters 

`x`  

The integer to convert, an instance of type `T`.

## Return Value

The value of `x` converted to type `U`.

## Discussion

Calling the `numericCast(_:)` function is equivalent to calling an initializer for the destination type. `numericCast(_:)` traps on overflow in `-O` and `-Onone` builds.

