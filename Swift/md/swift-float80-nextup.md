

- Swift
- Float80
-  nextUp 

Instance Property

# nextUp

The least representable value that compares greater than this value.

macOS 10.10+

``` source
var nextUp: Float80 { get }
```

## Discussion

For any finite value `x`, `x.nextUp` is greater than `x`. For `nan` or `infinity`, `x.nextUp` is `x` itself. The following special cases also apply:

- If `x` is `-infinity`, then `x.nextUp` is `-greatestFiniteMagnitude`.

- If `x` is `-leastNonzeroMagnitude`, then `x.nextUp` is `-0.0`.

- If `x` is zero, then `x.nextUp` is `leastNonzeroMagnitude`.

- If `x` is `greatestFiniteMagnitude`, then `x.nextUp` is `infinity`.

