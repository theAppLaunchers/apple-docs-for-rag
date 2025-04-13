

- Media Player
- MPNowPlayingInfoLanguageOption
-  languageOptionCharacteristics 

Instance Property

# languageOptionCharacteristics

The characteristics that describe the content of the language option.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+macOS 10.12.2+tvOS 9.0+visionOS 1.0+watchOS 5.0+

``` source
var languageOptionCharacteristics: [String]? { get }
```

## Discussion

This property contains an array of characteristics that describes the language option. See Language option characteristic constants for the most commonly used characteristics.

## See Also

### Retrieving language option properties

var displayName: String?

The display name for a language option.

var identifier: String?

The unique identifier for the language option.

var languageTag: String?

The abbreviated language code for the language option.

var languageOptionType: MPNowPlayingInfoLanguageOptionType

The type of language option.

enum MPNowPlayingInfoLanguageOptionType

The language option type to use for the Now Playing item.

