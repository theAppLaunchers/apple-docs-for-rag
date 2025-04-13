

- AppKit
- NSText
-  checkSpelling(\_:) 

Instance Method

# checkSpelling(\_:)

This action method searches for a misspelled word in the receiver’s text.

macOS

``` source
@MainActor
func checkSpelling(_ sender: Any?)
```

## Discussion

The search starts at the end of the selection and continues until it reaches a word suspected of being misspelled or the end of the text. If a word isn’t recognized by the spelling server, a showGuessPanel(_:) message then opens the Guess panel and allows the user to make a correction or add the word to the local dictionary.

## See Also

### Checking spelling

func showGuessPanel(Any?)

This action method opens the Spelling panel, allowing the user to make a correction during spell checking.

