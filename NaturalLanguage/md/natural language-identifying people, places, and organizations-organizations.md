

- Natural Language
-  Identifying people, places, and organizations 

Article

# Identifying people, places, and organizations

Use a linguistic tagger to perform named entity recognition on a string.

## Overview

Identifying named entities in natural language text can help make your app more intelligent. For example, a messaging app might look for names of people and places in text, to display related information like contact information or directions.

The example and accompanying steps below show how to use NLTagger to enumerate over natural language text and identify any named person, place, or organization.

1.  Create an instance of NLTagger, specifying nameType as the tag scheme to be used.

2.  Set the string property of the linguistic tagger to the natural language text.

3.  Create the options to omit punctuation, omit whitespace, and join names.

4.  Enumerate over the entire range of the string, specifying word as the tag unit and nameType as the tag scheme, and specifying the tagger options.

5.  In the enumeration block, if the tag is one of the types in `tags`, take a substring of the original text at `tokenRange` to obtain the named entity.

6.  To return multiple possible tags and their associated confidence scores, in the enumeration block, call the tagHypothesesAtIndex:unit:scheme:maximumCount:tokenRange: method.

7.  Run the following code to print out each name and its type, as well as other possible tags and their probabilities, on a new line.

```
let text = "The American Red Cross was established in Washington, D.C., by Clara Barton."

let tagger = NLTagger(tagSchemes: [.nameType])
tagger.string = text

let options: NLTagger.Options = [.omitPunctuation, .omitWhitespace, .joinNames]
let tags: [NLTag] = [.personalName, .placeName, .organizationName]

tagger.enumerateTags(in: text.startIndex..

## See Also

### Linguistic tags

Identifying parts of speech

Classify nouns, verbs, adjectives, and other parts of speech in a string.

class NLTagger

A tagger that analyzes natural language text.

