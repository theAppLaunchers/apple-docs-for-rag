

- Swift
- UInt128
-  %=(\_:\_:) 

Operator

# %=(\_:\_:)

Divides the first value by the second and stores the remainder in the left-hand-side variable.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+tvOS 18.0+visionOS 2.0+watchOS 11.0+

``` source
static func %= (a: inout UInt128, b: UInt128)
```

## Discussion

The result has the same sign as `lhs` and has a magnitude less than `rhs.magnitude`.

```
var x = 22
x %= 5
// x == 2

var y = 22
y %= -5
// y == 2

var z = -22
z %= -5
// z == -2
```

