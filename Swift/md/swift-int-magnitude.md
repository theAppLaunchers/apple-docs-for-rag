

- Swift
- Int
-  magnitude 

Instance Property

# magnitude

The magnitude of this value.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
var magnitude: UInt { get }
```

## Discussion

For any numeric value `x`, `x.magnitude` is the absolute value of `x`. You can use the `magnitude` property in operations that are simpler to implement in terms of unsigned values, such as printing the value of an integer, which is just printing a ‘-’ character in front of an absolute value.

```
let x = -200
// x.magnitude == 200
```

The global `abs(_:)` function provides more familiar syntax when you need to find an absolute value. In addition, because `abs(_:)` always returns a value of the same type, even in a generic context, using the function instead of the `magnitude` property is encouraged.

## See Also

### Finding the Sign and Magnitude

typealias Magnitude

A type that can represent the absolute value of any possible value of this type.

func abs&lt;T>(T) -> T

Returns the absolute value of the given number.

func signum() -> Int

Returns `-1` if this value is negative and `1` if it’s positive; otherwise, `0`.

