

- Swift
- UnsafeRawPointer
-  advanced(by:) 

Instance Method

# advanced(by:)

Returns a value that is offset the specified distance from this value.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func advanced(by n: Int) -> UnsafeRawPointer
```

## Parameters 

`n`  

The distance to advance this value.

## Return Value

A value that is offset from this value by `n`.

## Discussion

Use the `advanced(by:)` method in generic code to offset a value by a specified distance. If you’re working directly with numeric values, use the addition operator (`+`) instead of this method.

```
func addOne(to x: T) -> T
    where T.Stride: ExpressibleByIntegerLiteral
{
    return x.advanced(by: 1)
}

let x = addOne(to: 5)
// x == 6
let y = addOne(to: 3.5)
// y = 4.5
```

If this type’s `Stride` type conforms to `BinaryInteger`, then for a value `x`, a distance `n`, and a value `y = x.advanced(by: n)`, `x.distance(to: y) == n`. Using this method with types that have a noninteger `Stride` may result in an approximation. If the result of advancing by `n` is not representable as a value of this type, then a runtime error may occur.

Complexity

O(1)

