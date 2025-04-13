

- Foundation
- NSLinguisticTagger
-  possibleTags(at:scheme:tokenRange:sentenceRange:scores:) Deprecated

Instance Method

# possibleTags(at:scheme:tokenRange:sentenceRange:scores:)

Returns an array of possible tags for the given scheme at the specified range, supplying matching scores.

iOS 5.0–18.4DeprecatediPadOS 5.0–18.4DeprecatedMac Catalyst 13.1+macOS 10.7–15.4DeprecatedtvOS 9.0–18.4DeprecatedvisionOS 1.0–2.4DeprecatedwatchOS 2.0–9.0Deprecated

``` source
func possibleTags(
    at charIndex: Int,
    scheme tagScheme: String,
    tokenRange: NSRangePointer?,
    sentenceRange: NSRangePointer?,
    scores: AutoreleasingUnsafeMutablePointer?
) -> [String]?
```

Deprecated

All NSLinguisticTagger API should be replaced with NaturalLanguage.framework API

## Parameters 

`charIndex`  

The position of the initial character.

`tagScheme`  

The tag scheme. See NSLinguisticTagScheme for possible values.

`tokenRange`  

The token range.

`sentenceRange`  

The range of the sentence.

`scores`  

Returns by reference an array of numeric scores indicating the likelihood that the range matches the tag scheme.

## Return Value

Returns an array of possible tags for the tag scheme at the specified location, starting with the most likely tag scheme. For some tag schemes only a single tag will be returned, but for others a list of possibilities will be provided.

## Discussion

Calling this method is not recommended; for most use cases, this information is not as useful as what is provided by the methods described in Enumerating Linguistic Tags and Getting Linguistic Tags.

