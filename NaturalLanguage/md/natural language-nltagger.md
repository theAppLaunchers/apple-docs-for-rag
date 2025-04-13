

- Natural Language
-  NLTagger 

Class

# NLTagger

A tagger that analyzes natural language text.

iOS 12.0+iPadOS 12.0+Mac Catalyst 13.1+macOS 10.14+tvOS 12.0+visionOS 1.0+watchOS 5.0+

``` source
class NLTagger
```

## Mentioned in 

Identifying people, places, and organizations

Identifying parts of speech

Creating a word tagger model

## Overview

NLTagger supports many different languages and scripts. Use it to segment natural language text into paragraph, sentence, or word units and to tag each unit with information like part of speech, lexical class, lemma, script, and language.

When you create a linguistic tagger, you specify what kind of information you’re interested in by passing one or more NLTagScheme values. Set the string property to the natural language text you want to analyze, and the linguistic tagger processes it according to the specified tag schemes. You can then enumerate over the tags in a specified range, using the methods described in Enumerating linguistic tags, to get the information requested for a given scheme and unit.

Important

Don’t use an instance of NLTagger simultaneously from multiple threads.

## Topics

### Creating a tagger

init(tagSchemes: [NLTagScheme])

Creates a linguistic tagger instance using the specified tag schemes and options.

var string: String?

The string being analyzed by the linguistic tagger.

### Getting the tag schemes

class func availableTagSchemes(for: NLTokenUnit, language: NLLanguage) -> [NLTagScheme]

Retrieves the tag schemes available for a particular unit (like word or sentence) and language on the current device.

class func requestAssets(for: NLLanguage, tagScheme: NLTagScheme, completionHandler: (NLTagger.AssetsResult, (any Error)?) -> Void)

Asks the Natural Language framework to load any missing assets for a tag scheme onto the device for the given language.

enum AssetsResult

The response to an asset request.

var tagSchemes: [NLTagScheme]

The tag schemes configured for this linguistic tagger.

struct NLTagScheme

Constants for the tag schemes specified when initializing a linguistic tagger.

### Determining the dominant language and orthography

var dominantLanguage: NLLanguage?

The dominant language of the string set for the linguistic tagger.

func setLanguage(NLLanguage, range: Range&lt;String.Index>)

Sets the language for a range of text within the tagger’s string.

func setOrthography(NSOrthography, range: Range&lt;String.Index>)

Sets the orthography for the specified range.

### Enumerating linguistic tags

func enumerateTags(in: Range&lt;String.Index>, unit: NLTokenUnit, scheme: NLTagScheme, options: NLTagger.Options, using: (NLTag?, Range&lt;String.Index>) -> Bool)

Enumerates a block over the tagger’s string, given a range, token unit, and tag scheme.

struct Options

Constants for linguistic tagger enumeration specifying which tokens to omit and whether to join names.

struct NLTag

A token type, lexical class, name, lemma, language, or script returned by a linguistic tagger for natural language text.

### Getting linguistic tags

func tags(in: Range&lt;String.Index>, unit: NLTokenUnit, scheme: NLTagScheme, options: NLTagger.Options) -> [(NLTag?, Range&lt;String.Index>)]

Finds an array of linguistic tags and token ranges for a given string range and linguistic unit.

func tag(at: String.Index, unit: NLTokenUnit, scheme: NLTagScheme) -> (NLTag?, Range&lt;String.Index>)

Finds a tag for a given linguistic unit, for a single scheme, at the specified character position.

func tagHypotheses(at: String.Index, unit: NLTokenUnit, scheme: NLTagScheme, maximumCount: Int) -> ([String : Double], Range&lt;String.Index>)

Finds multiple possible tags for a given linguistic unit, for a single scheme, at the specified character position.

### Determining the range of a unit token

func tokenRange(at: String.Index, unit: NLTokenUnit) -> Range&lt;String.Index>

Returns the range of the linguistic unit containing the specified character index.

func tokenRange(for: Range&lt;String.Index>, unit: NLTokenUnit) -> Range&lt;String.Index>

Finds the entire range of all tokens of the specified linguistic unit contained completely or partially within the specified range.

enum NLTokenUnit

Constants representing linguistic units.

### Using models with a tagger

func setModels([NLModel], forTagScheme: NLTagScheme)

Assigns models for a tag scheme.

func models(forTagScheme: NLTagScheme) -> [NLModel]

Returns the models that apply to the given tag scheme.

### Using gazetteers with a tagger

func setGazetteers([NLGazetteer], for: NLTagScheme)

Attaches gazetteers to a tag scheme, typically one gazetteer per language or one language-independent gazetteer.

func gazetteers(for: NLTagScheme) -> [NLGazetteer]

Retrieves the gazetteers attached to a tag scheme.

class NLGazetteer

A collection of terms and their labels, which take precedence over a word tagger.

## Relationships

### Inherits From

- NSObject

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSObjectProtocol

## See Also

### Linguistic tags

Identifying parts of speech

Classify nouns, verbs, adjectives, and other parts of speech in a string.

Identifying people, places, and organizations

Use a linguistic tagger to perform named entity recognition on a string.

