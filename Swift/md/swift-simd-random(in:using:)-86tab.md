

- Swift
- SIMD
-  random(in:using:) 

Type Method

# random(in:using:)

Returns a vector with random values from within the specified range in all lanes, using the given generator as a source for randomness.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
static func random(
    in range: Range,
    using generator: inout T
) -> Self where T : RandomNumberGenerator
```

Available when `Scalar` conforms to `BinaryFloatingPoint` and `Scalar.RawSignificand` conforms to `FixedWidthInteger`.

