

- Swift
- RangeReplaceableCollection
-  replace(with:maxReplacements:content:) 

Instance Method

# replace(with:maxReplacements:content:)

Replaces all matches for the regex in this collection, using the given closure to create the regex.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+watchOS 9.0+

``` source
mutating func replace(
    with replacement: Replacement,
    maxReplacements: Int = .max,
    @RegexComponentBuilder content: () -> some RegexComponent
) where Replacement : Collection, Replacement.Element == Character
```

Available when `Self` conforms to `BidirectionalCollection` and `SubSequence` is `Substring`.

## Parameters 

`replacement`  

The new elements to add to the collection in place of each match for the regex, using `content` to create the regex.

`maxReplacements`  

A number specifying how many occurrences of the regex to replace.

`content`  

A closure that returns the collection to search for and replace.

