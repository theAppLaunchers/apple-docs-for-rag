

- Core HID
- HIDReportID
-  \>=(\_:\_:) 

Operator

# \>=(\_:\_:)

Returns a Boolean value indicating whether the value of the first argument is greater than or equal to that of the second argument.

Core HIDSwiftmacOS 15.0+

``` source
static func >= (lhs: Self, rhs: Self) -> Bool
```

## Parameters 

`lhs`  

A value to compare.

`rhs`  

Another value to compare.

## Return Value

`true` if `lhs` is greater than or equal to `rhs`; otherwise, `false`.

## Discussion

This is the default implementation of the greater-than-or-equal-to operator (`>=`) for any type that conforms to `Comparable`.

