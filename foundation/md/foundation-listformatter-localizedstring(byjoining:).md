

- Foundation
- ListFormatter
-  localizedString(byJoining:) 

Type Method

# localizedString(byJoining:)

Constructs a formatted string from an array of strings that uses the list format specific to the current locale.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.1+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
class func localizedString(byJoining strings: [String]) -> String
```

## Parameters 

`strings`  

An array of strings to join together in a list.

## Return Value

A formatted string that joins together a list of strings using a locale-specific list format.

## Discussion

Tip

Use this method to join strings that are ready to be displayed in a bullet-point list. Sentences, phrases with punctuations, and appositions may not work well when joined together.

## See Also

### Converting Arrays to Formatted Lists

func string(from: [Any]) -> String?

Creates a formatted string for an array of items.

func string(for: Any?) -> String?

Creates a formatted string for an array of items.

