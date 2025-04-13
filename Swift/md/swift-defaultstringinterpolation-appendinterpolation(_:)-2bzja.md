

- Swift
- DefaultStringInterpolation
-  appendInterpolation(\_:) 

Instance Method

# appendInterpolation(\_:)

Interpolates the given value’s textual representation into the string literal being created.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
mutating func appendInterpolation(_ value: T) where T : CustomStringConvertible, T : TextOutputStreamable
```

## Discussion

Do not call this method directly. It is used by the compiler when interpreting string interpolations. Instead, use string interpolation to create a new string by including values, literals, variables, or expressions enclosed in parentheses, prefixed by a backslash (`\(`…`)`).

```
let price = 2
let number = 3
let message = """
              If one cookie costs \(price) dollars, \
              \(number) cookies cost \(price * number) dollars.
              """
print(message)
// Prints "If one cookie costs 2 dollars, 3 cookies cost 6 dollars."
```

