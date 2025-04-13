

- Swift
- Int
-  +(\_:) 

Operator

# +(\_:)

Returns the given number unchanged.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
static func + (x: Self) -> Self
```

## Return Value

The given argument without any changes.

## Discussion

You can use the unary plus operator (`+`) to provide symmetry in your code for positive numbers when also using the unary minus operator.

```
let x = -21
let y = +21
// x == -21
// y == 21
```

