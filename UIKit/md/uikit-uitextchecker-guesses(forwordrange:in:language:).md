

- UIKit
- UITextChecker
-  guesses(forWordRange:in:language:) 

Instance Method

# guesses(forWordRange:in:language:)

Returns a list of words that are possible valid replacements for a misspelled word.

iOS 3.2+iPadOS 3.2+Mac Catalyst 13.1+tvOSvisionOS 1.0+

``` source
@MainActor
func guesses(
    forWordRange range: NSRange,
    in string: String,
    language: String
) -> [String]?
```

## Parameters 

`range`  

The range of a misspelled word in `string`.

`string`  

A string in which there is a misspelled word, as located by `range`.

`language`  

The language of the of the words that are possible corrections. This string is from the ISO 639-1 standard, for example `es` (Spanish).

## Return Value

An array of strings each of which might be a correct substitute (that is, a guess) for a misspelled word in the given range of the string. If no possible guesses are found, the method returns an empty array.

## Discussion

The strings in the array are in the order they should be presented to the user—that is, more probable guesses come first in the array.

## See Also

### Obtaining Word Guesses and Completions

func completions(forPartialWordRange: NSRange, in: String, language: String) -> [String]?

Returns an array of strings that are possible completions for a partially entered word.

