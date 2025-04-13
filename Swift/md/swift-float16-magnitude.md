

- Swift
- Float16
-  magnitude 

Instance Property

# magnitude

The magnitude of this value.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+macOS 11.0+tvOS 14.0+visionOS 1.0+watchOS 7.0+

``` source
var magnitude: Float16 { get }
```

## Discussion

For any numeric value `x`, `x.magnitude` is the absolute value of `x`. You can use the `magnitude` property in operations that are simpler to implement in terms of unsigned values, such as printing the value of an integer, which is just printing a ‘-’ character in front of an absolute value.

```
let x = -200
// x.magnitude == 200
```

The global `abs(_:)` function provides more familiar syntax when you need to find an absolute value. In addition, because `abs(_:)` always returns a value of the same type, even in a generic context, using the function instead of the `magnitude` property is encouraged.

