

- Swift
- Bool
-  &&(\_:\_:) 

Operator

# &&(\_:\_:)

Performs a logical AND operation on two Boolean values.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
static func && (lhs: Bool, rhs: @autoclosure () throws -> Bool) rethrows -> Bool
```

## Parameters 

`lhs`  

The left-hand side of the operation.

`rhs`  

The right-hand side of the operation.

## Discussion

The logical AND operator (`&&`) combines two Boolean values and returns `true` if both of the values are `true`. If either of the values is `false`, the operator returns `false`.

This operator uses short-circuit evaluation: The left-hand side (`lhs`) is evaluated first, and the right-hand side (`rhs`) is evaluated only if `lhs` evaluates to `true`. For example:

```
let measurements = [7.44, 6.51, 4.74, 5.88, 6.27, 6.12, 7.76]
let sum = measurements.reduce(0, +)

if measurements.count > 0 && sum / Double(measurements.count) 

In this example, `lhs` tests whether `measurements.count` is greater than zero. Evaluation of the `&&` operator is one of the following:

- When `measurements.count` is equal to zero, `lhs` evaluates to `false` and `rhs` is not evaluated, preventing a divide-by-zero error in the expression `sum / Double(measurements.count)`. The result of the operation is `false`.

- When `measurements.count` is greater than zero, `lhs` evaluates to `true` and `rhs` is evaluated. The result of evaluating `rhs` is the result of the `&&` operation.

## See Also

### Transforming a Boolean

func toggle()

Toggles the Boolean variable’s value.

static func ! (Bool) -> Bool

Performs a logical NOT operation on a Boolean value.

static func || (Bool, @autoclosure () throws -> Bool) rethrows -> Bool

Performs a logical OR operation on two Boolean values.

