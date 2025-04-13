

- Swift
- Float80
-  description 

Instance Property

# description

A textual representation of the value.

macOS 10.10+

``` source
var description: String { get }
```

## Discussion

For any finite value, this property provides a string that can be converted back to an instance of `Float80` without rounding errors. That is, if `x` is an instance of `Float80`, then `Float80(x.description) == x` is always true. For any NaN value, the property’s value is “nan”, and for positive and negative infinity its value is “inf” and “-inf”.

