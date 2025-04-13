

- Swift
- Float
-  init(\_:) 

Initializer

# init(\_:)

Creates a new instance from the given string.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
init?(_ text: S) where S : StringProtocol
```

## Parameters 

`text`  

An input string to convert to a `Float?` instance.

## Discussion

The string passed as `text` can represent a real number in decimal or hexadecimal format or can be in a special format representing infinity or NaN (“not a number”). If `text` is not in a recognized format, the optional initializer will fail and return `nil`.

The `text` string consists of an optional plus or minus sign character (`+` or `-`) followed by one of the following:

- A *decimal string* contains a significand consisting of one or more decimal digits that may include a decimal point:

  ```
  let c = Float("-1.0")
  // c == -1.0

  let d = Float("28.375")
  // d == 28.375
  ```

  A decimal string may also include an exponent following the significand, indicating the power of 10 by which the significand should be multiplied. If included, the exponent is separated by a single character, `e` or `E`, and consists of an optional plus or minus sign character and a sequence of decimal digits.

  ```
  let e = Float("2837.5e-2")
  // e == 28.375
  ```

- A *hexadecimal string* contains a significand consisting of `0X` or `0x` followed by one or more hexadecimal digits that may include a decimal point.

  ```
  let f = Float("0x1c.6")
  // f == 28.375
  ```

  A hexadecimal string may also include an exponent indicating the power of 2 by which the significand should be multiplied. If included, the exponent is separated by a single character, `p` or `P`, and consists of an optional plus or minus sign character and a sequence of decimal digits.

  ```
  let g = Float("0x1.c6p4")
  // g == 28.375
  ```

- The input strings `"inf"` or `"infinity"` (case insensitive) are converted to an infinite result:

  ```
  let i = Float("inf")
  // i == Float.infinity

  let j = Float("-Infinity")
  // j == -Float.infinity
  ```

- An input string of `"nan"` (case insensitive) is converted into a *NaN* value:

  ```
  let n = Float("-nan")
  // n?.isNaN == true
  // n?.sign == .minus
  ```

  A NaN string may also include a payload in parentheses following the `"nan"` keyword. The payload consists of a sequence of decimal digits, or the characters `0X` or `0x` followed by a sequence of hexadecimal digits. If the payload contains any other characters, it is ignored. If the value of the payload is larger than can be stored as the payload of a `Float.nan`, the least significant bits are used.

  ```
  let p = Float("nan(0x10)")
  // p?.isNaN == true
  // String(p!) == "nan(0x10)"
  ```

A string in any other format than those described above or containing additional characters results in a `nil` value. For example, the following conversions result in `nil`:

```
  Float(" 5.0")      // Includes whitespace
  Float("±2.0")      // Invalid character
  Float("0x1.25e4")  // Incorrect exponent format
```

A decimal or hexadecimal string is converted to a `Float` instance using the IEEE 754 roundTiesToEven (default) rounding attribute. Values with absolute value smaller than `Float.leastNonzeroMagnitude` are rounded to plus or minus zero. Values with absolute value larger than `Float.greatestFiniteMagnitude` are rounded to plus or minus infinity.

```
  let y = Float("1.23e-9999")
  // y == 0.0
  // y?.sign == .plus

  let z = Float("-7.89e-7206")
  // z == -0.0
  // z?.sign == .minus

  let r = Float("1.23e17802")
  // r == Float.infinity

  let s = Float("-7.89e7206")
  // s == Float.-infinity
```

Note

Prior to Swift 5.4, a decimal or hexadecimal input string whose value was too large to represent as a finite `Float` instance returned `nil` instead of `Float.infinity`.

## See Also

### Converting Strings

init?(Substring)

