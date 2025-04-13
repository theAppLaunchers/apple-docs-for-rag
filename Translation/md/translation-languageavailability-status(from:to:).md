

- Translation
- LanguageAvailability
-  status(from:to:) 

Instance Method

# status(from:to:)

Checks to see if a specific language pairing is installed and ready for translation.

iOS 18.0+iPadOS 18.0+macOS 15.0+

``` source
func status(
    from source: Locale.Language,
    to target: Locale.Language?
) async -> LanguageAvailability.Status
```

## Parameters 

`source`  

The source language of the content.

`target`  

The target language you want to translate content into. When set to `nil` the system picks an appropriate target based on the user’s preferred languages and returns the status for those languages.

## Return Value

The availability status for a language pairing.

## Discussion

Use this function to determine whether the language assets the device requires for translation have downloaded.

Note

The framework doesn’t support translating from and to the same language. For example you can’t translate from English (US) to English (UK).

## See Also

### Checking availability

func status(for: String, to: Locale.Language?) async throws -> LanguageAvailability.Status

Checks to see if a language pairing is supported based off a string of sample text.

enum Status

The availability status for a language or language pairing.

