

- Natural Language
- NLTagger
-  tagSchemes 

Instance Property

# tagSchemes

The tag schemes configured for this linguistic tagger.

iOS 12.0+iPadOS 12.0+Mac Catalyst 13.1+macOS 10.14+tvOS 12.0+visionOS 1.0+watchOS 5.0+

``` source
var tagSchemes: [NLTagScheme] { get }
```

## See Also

### Getting the tag schemes

class func availableTagSchemes(for: NLTokenUnit, language: NLLanguage) -> [NLTagScheme]

Retrieves the tag schemes available for a particular unit (like word or sentence) and language on the current device.

class func requestAssets(for: NLLanguage, tagScheme: NLTagScheme, completionHandler: (NLTagger.AssetsResult, (any Error)?) -> Void)

Asks the Natural Language framework to load any missing assets for a tag scheme onto the device for the given language.

enum AssetsResult

The response to an asset request.

struct NLTagScheme

Constants for the tag schemes specified when initializing a linguistic tagger.

