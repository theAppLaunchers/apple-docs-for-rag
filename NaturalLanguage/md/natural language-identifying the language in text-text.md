

- Natural Language
-  Identifying the language in text 

Article

# Identifying the language in text

Detect the language in a piece of text by using a language recognizer.

## Overview

*Language identification* is the task of automatically detecting the language and script of a piece of text. In Natural Language, NLLanguageRecognizer performs this task.

Using a language recognizer, you can obtain the most likely language for a piece of input text, or a set of possible language candidates with their associated probabilities. You can also constrain the identification process by providing a list of hints about known probabilities for languages, or a list of languages the predictions are constrained against. You’ll find supported languages in NLLanguage, but you can also define and use your own language tags.

### Configure a language recognizer

To set up a language recognizer, create an instance of NLLanguageRecognizer. Call its processString(_:) method with the input text you want to perform language identification for. If your text has multiple parts that you want to analyze together, call processString(_:) with an input string for each part before you ask for the language prediction.

```
// Create a language recognizer.
let recognizer = NLLanguageRecognizer()
recognizer.processString("This is a test, mein Freund.")
```

### Get the most likely language

To get the most likely language for the provided input text, access the language recognizer’s dominantLanguage property. This property is an optional value, so make sure to handle the case where the language recognizer can’t identify a dominant language.

```
// Identify the dominant language.
if let language = recognizer.dominantLanguage {
    print(language.rawValue)
} else {
    print("Language not recognized")
}
```

### Get the possible languages

To generate multiple possible language predictions, use the languageHypothesesWithMaximum: method. Specify the maximum number of possible languages to identify.

```
// Generate up to two language hypotheses.
let hypotheses = recognizer.languageHypotheses(withMaximum: 2)
print(hypotheses)
```

### Constrain the language identification

Although this step isn’t required, you can provide the language recognizer with information about the text you want to identify if you already know something about it. For example, if you know that the language must be within a specific set of languages, you can specify that constraint.

Specifically, you can provide either or both of these constraints:

- A list of languages the predictions are constrained against

- A list of known probabilities for some or all languages

```
// Specify constraints for language identification.
recognizer.languageConstraints = [.french, .english, .german,
                                  .italian, .spanish, .portuguese]

recognizer.languageHints = [.french: 0.5,
                            .english: 0.9,
                            .german: 0.8,
                            .italian: 0.6,
                            .spanish: 0.3,
                            .portuguese: 0.2]

let constrainedHypotheses = recognizer.languageHypotheses(withMaximum: 2)
print(constrainedHypotheses)
```

### Identify the Language for Multiple Texts

If you have distinct pieces of text whose languages you want to identify separately, you need to reset the recognizer before processing the next string. Resetting the language recognizer returns it to its initial state, removing any input strings, language constraints, and hints that you previously provided.

```
// Reset the recognizer to its initial state.
recognizer.reset()

// Process additional strings for language identification.
recognizer.processString("Este es un idioma diferente.")
```

## See Also

### Language identification

class NLLanguageRecognizer

The language of a body of text.

struct NLLanguage

The languages that the Natural Language framework supports.

