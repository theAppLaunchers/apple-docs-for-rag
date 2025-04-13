

- Media Player
- MPChangeLanguageOptionCommandEvent
-  languageOption 

Instance Property

# languageOption

The requested language option to change.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+macOS 10.12.2+tvOS 9.0+visionOS 1.0+watchOS 5.0+

``` source
var languageOption: MPNowPlayingInfoLanguageOption { get }
```

## Discussion

The supplied language option may be the Automatic Legible Language Option, which requests the best legible language based on the user’s preferences. See isAutomaticLegibleLanguageOption().

## See Also

### Changing the language option

var setting: MPChangeLanguageOptionSetting

The extent of the language setting change.

enum MPChangeLanguageOptionSetting

The states that determine when language option changes take effect.

