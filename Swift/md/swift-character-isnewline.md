

- Swift
- Character
-  isNewline 

Instance Property

# isNewline

A Boolean value indicating whether this character represents a newline.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
var isNewline: Bool { get }
```

## Discussion

For example, the following characters all represent newlines:

- “\n” (U+000A): LINE FEED (LF)

- U+000B: LINE TABULATION (VT)

- U+000C: FORM FEED (FF)

- “\r” (U+000D): CARRIAGE RETURN (CR)

- “\r\n” (U+000D U+000A): CR-LF

- U+0085: NEXT LINE (NEL)

- U+2028: LINE SEPARATOR

- U+2029: PARAGRAPH SEPARATOR

## See Also

### Inspecting a Character

var isLetter: Bool

A Boolean value indicating whether this character is a letter.

var isPunctuation: Bool

A Boolean value indicating whether this character represents punctuation.

var isWhitespace: Bool

A Boolean value indicating whether this character represents whitespace, including newlines.

var isSymbol: Bool

A Boolean value indicating whether this character represents a symbol.

var isMathSymbol: Bool

A Boolean value indicating whether this character represents a symbol that naturally appears in mathematical contexts.

var isCurrencySymbol: Bool

A Boolean value indicating whether this character represents a currency symbol.

