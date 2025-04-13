

- Foundation
- NSSpellServerDelegate
-  spellServer(\_:recordResponse:toCorrection:forWord:language:) 

Instance Method

# spellServer(\_:recordResponse:toCorrection:forWord:language:)

Notifies the spell checker of the users’s response to a correction.

macOS 10.7+

``` source
optional func spellServer(
    _ sender: NSSpellServer,
    recordResponse response: Int,
    toCorrection correction: String,
    forWord word: String,
    language: String
)
```

## Parameters 

`sender`  

The spell server.

`response`  

The user’s response.

`correction`  

The corrected word. This should match the original correction.

`word`  

The original word. This should match the original correction.

`language`  

The language being edited. This should match the original correction.

## Discussion

When the user accepts, rejects, or edits an autocorrection, the view notifies the NSSpellChecker class of what happened in the client application, and `NSSpellChecker` then invokes this method, so that it can record that and modify future autocorrection behavior based on what it has learned from the user’s actions.

## See Also

### Managing the Spelling Dictionary

func spellServer(NSSpellServer, didForgetWord: String, inLanguage: String)

Notifies the delegate that the sender has removed the specified word from the user’s list of acceptable words in the specified language.

func spellServer(NSSpellServer, didLearnWord: String, inLanguage: String)

Notifies the delegate that the sender has added the specified word to the user’s list of acceptable words in the specified language.

func spellServer(NSSpellServer, suggestCompletionsForPartialWordRange: NSRange, in: String, language: String) -> [String]?

This delegate method returns an array of possible word completions from the spell checker, based on a partially completed string and a given range.

