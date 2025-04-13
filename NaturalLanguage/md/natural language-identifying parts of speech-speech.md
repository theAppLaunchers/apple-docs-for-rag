

- Natural Language
-  Identifying parts of speech 

Article

# Identifying parts of speech

Classify nouns, verbs, adjectives, and other parts of speech in a string.

## Overview

Identifying the parts of speech for words in natural language text can help your program understand the meaning of sentences. For example, provided the transcription of a request spoken by the user, you might programmatically determine general intent by looking at only the nouns and verbs.

The example below shows how to use NLTagger to enumerate over natural language text and identify the part of speech for each word.

```
let text = "The ripe taste of cheese improves with age."
let tagger = NLTagger(tagSchemes: [.lexicalClass])
tagger.string = text
let options: NLTagger.Options = [.omitPunctuation, .omitWhitespace]
tagger.enumerateTags(in: text.startIndex..

1.  Create an instance of NLTagger, specifying lexicalClass as the tag scheme to be used.

2.  Set the string property of the linguistic tagger to the natural language text.

3.  Create the options to omit punctuation and whitespace.

4.  Enumerate over the entire range of the string, specifying word as the tag unit and lexicalClass as the tag scheme, and the tagger options.

5.  In the enumeration block, take a substring of the original text at `tokenRange` to obtain each word.

6.  Run this code to print out each word and its part of speech on a new line.

## See Also

### Linguistic tags

Identifying people, places, and organizations

Use a linguistic tagger to perform named entity recognition on a string.

class NLTagger

A tagger that analyzes natural language text.

