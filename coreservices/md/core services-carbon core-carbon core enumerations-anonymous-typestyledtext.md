

- Core Services
- Carbon Core
- Carbon Core Enumerations
- Anonymous
-  typeStyledText 

Global Variable

# typeStyledText

Mac Catalyst 13.0+macOS 10.0+

``` source
var typeStyledText: DescType { get }
```

## Discussion

Text that includes style information.

Styled text is stored as a record, in which the styles have the key `'ksty'` and the plain text is has the key '`ktxt'`. You can use this information to extract plain text from styled text without coercion.

However, getting rid of the style information, with or without coercion, may corrupt the text, since the styles imply what encoding to use. In fact, use of `typeText` and `typeStyledText` are not recommended, starting with macOS, because they are not safe with international characters—you should use one of the Unicode text types instead.

For important information, see the Version Notes section of the typeUnicodeText enum.

