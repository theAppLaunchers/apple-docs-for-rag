

- Foundation
- NSCharacterSet
-  lowercaseLetters 

Type Property

# lowercaseLetters

A character set containing the characters in Unicode General Category Ll.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.0+macOS 10.0+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
class var lowercaseLetters: CharacterSet { get }
```

## Return Value

A character set containing all the lowercase letter characters.

## Discussion

Informally, this set is the set of all characters used as lowercase letters in alphabets that make case distinctions.

## See Also

### Getting Standard Character Sets

class var alphanumerics: CharacterSet

A character set containing the characters in Unicode General Categories L\*, M\*, and N\*.

class var capitalizedLetters: CharacterSet

A character set containing the characters in Unicode General Category Lt.

class var controlCharacters: CharacterSet

A character set containing the characters in Unicode General Category Cc and Cf.

class var decimalDigits: CharacterSet

A character set containing the characters in the category of Decimal Numbers.

class var decomposables: CharacterSet

A character set containing individual Unicode characters that can also be represented as composed character sequences (such as for letters with accents), by the definition of “standard decomposition” in version 3.2 of the Unicode character encoding standard.

class var illegalCharacters: CharacterSet

A character set containing values in the category of Non-Characters or that have not yet been defined in version 3.2 of the Unicode standard.

class var letters: CharacterSet

A character set containing the characters in Unicode General Category L\* & M\*.

class var newlines: CharacterSet

A character set containing the newline characters (`U+000A` ~ `U+000D`, `U+0085`, `U+2028`, and `U+2029`).

class var nonBaseCharacters: CharacterSet

A character set containing the characters in Unicode General Category M\*.

class var punctuationCharacters: CharacterSet

A character set containing the characters in Unicode General Category P\*.

class var symbols: CharacterSet

A character set containing the characters in Unicode General Category S\*.

class var uppercaseLetters: CharacterSet

A character set containing the characters in Unicode General Category Lu and Lt.

class var whitespacesAndNewlines: CharacterSet

A character set containing characters in Unicode General Category Z\*, `U+000A` ~ `U+000D`, and `U+0085`.

class var whitespaces: CharacterSet

A character set containing the characters in Unicode General Category Zs and `CHARACTER TABULATION` (`U+0009`).

