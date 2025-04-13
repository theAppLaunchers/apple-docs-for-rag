

- AVFoundation
- AVMediaSelectionGroup
-  mediaSelectionOptions(from:filteredAndSortedAccordingToPreferredLanguages:) 

Type Method

# mediaSelectionOptions(from:filteredAndSortedAccordingToPreferredLanguages:)

Returns an array of media selection options, filtering them according to whether their locales match one of the specified languages.

iOS 6.0+iPadOS 6.0+Mac Catalyst 13.1+macOS 10.8+tvOS 9.0+visionOS 1.0+watchOS 1.0+

``` source
class func mediaSelectionOptions(
    from mediaSelectionOptions: [AVMediaSelectionOption],
    filteredAndSortedAccordingToPreferredLanguages preferredLanguages: [String]
) -> [AVMediaSelectionOption]
```

## Parameters 

`mediaSelectionOptions`  

An array of AVMediaSelectionOption objects to be filtered and sorted.

`preferredLanguages`  

An array of NSString objects, each of which contains a canonicalized IETF BCP 47 language identifier. The strings should be sorted in order of preference, with the string corresponding to the most preferred language as the first element in the array. Typically, you retrieve these strings using the preferredLanguages class method of the NSLocale class.

## Return Value

An array of AVMediaSelectionOption objects that match one of the languages in the `preferredLanguages` parameter. The objects in this array are sorted based on the language each one matches, with objects matching the most preferred language first in the array.

## See Also

### Filtering Selection Options

class func playableMediaSelectionOptions(from: [AVMediaSelectionOption]) -> [AVMediaSelectionOption]

Returns an array containing the media selection options from a given array that are playable.

class func mediaSelectionOptions(from: [AVMediaSelectionOption], with: Locale) -> [AVMediaSelectionOption]

Returns an array containing the media selection options from a given array that match the specified locale.

class func mediaSelectionOptions(from: [AVMediaSelectionOption], withMediaCharacteristics: [AVMediaCharacteristic]) -> [AVMediaSelectionOption]

Returns an array containing the media selection options from a given array that match given media characteristics.

class func mediaSelectionOptions(from: [AVMediaSelectionOption], withoutMediaCharacteristics: [AVMediaCharacteristic]) -> [AVMediaSelectionOption]

Returns an array containing the media selection options from a given array that do not match given media characteristics.

