

- AppKit
- NSTextView
-  isContinuousSpellCheckingEnabled 

Instance Property

# isContinuousSpellCheckingEnabled

A Boolean value that indicates whether the receiver has continuous spell checking enabled.

macOS

``` source
@MainActor
var isContinuousSpellCheckingEnabled: Bool { get set }
```

## See Also

### Working with the spelling checker

var spellCheckerDocumentTag: Int

A tag identifying the text view’s text as a document for the spell checker server.

func toggleContinuousSpellChecking(Any?)

Toggles whether continuous spell checking is enabled for the receiver.

var isGrammarCheckingEnabled: Bool

Enables and disables grammar checking.

func toggleGrammarChecking(Any?)

Changes the state of grammar checking from enabled to disabled and vice versa.

func setSpellingState(Int, range: NSRange)

Sets the spelling state, which controls the display of the spelling and grammar indicators on the given text range.

