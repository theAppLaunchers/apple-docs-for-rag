

- Swift
- Int32
-  ~(\_:) 

Operator

# ~(\_:)

Returns the inverse of the bits set in the argument.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
static func ~ (x: Self) -> Self
```

## Discussion

The bitwise NOT operator (`~`) is a prefix operator that returns a value in which all the bits of its argument are flipped: Bits that are `1` in the argument are `0` in the result, and bits that are `0` in the argument are `1` in the result. This is equivalent to the inverse of a set. For example:

```
let x: UInt8 = 5        // 0b00000101
let notX = ~x           // 0b11111010
```

Performing a bitwise NOT operation on 0 returns a value with every bit set to `1`.

```
let allOnes = ~UInt8.min   // 0b11111111
```

Complexity

O(1).

