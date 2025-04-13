

- Swift
- SIMDMask
-  .!=(\_:\_:) 

Operator

# .!=(\_:\_:)

A vector mask with the result of a pointwise inequality comparison.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
static func .!= (a: SIMDMask, b: SIMDMask) -> SIMDMask
```

Available when `Storage` is `SIMD64`.

## Discussion

Equivalent to:

```
var result = SIMDMask>()
for i in result.indices {
  result[i] = a[i] != b[i]
}
```

