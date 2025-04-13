

- Core Foundation
-  CFStringGetHyphenationLocationBeforeIndex(\_:\_:\_:\_:\_:\_:) 

Function

# CFStringGetHyphenationLocationBeforeIndex(\_:\_:\_:\_:\_:\_:)

Retrieve the first potential hyphenation location found before the specified location.

iOS 4.2+iPadOS 4.2+Mac Catalyst 13.1+macOS 10.7+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func CFStringGetHyphenationLocationBeforeIndex(
    _ string: CFString!,
    _ location: CFIndex,
    _ limitRange: CFRange,
    _ options: CFOptionFlags,
    _ locale: CFLocale!,
    _ character: UnsafeMutablePointer!
) -> CFIndex
```

## Parameters 

`string`  

The string to be hyphenated. If this parameter is not a valid CFString object, the behavior is undefined.

`location`  

An index in the string. If a valid hyphen index is returned, it will be before this index.

`limitRange`  

The range of characters within the string to search. If the range location or end point (defined by the location plus length minus 1) are outside the index space of the string (0 to N-1 inclusive, where N is the length of the string), the behavior is undefined. If the range length is negative, the behavior is undefined. The range may be empty (length 0), in which case no hyphen location is generated.

`options`  

Reserved for future use.

`locale`  

A valid locale that specifies which language’s hyphenation conventions to use. Hyphenation data is not available for all locales. You can use CFStringIsHyphenationAvailableForLocale(_:) to test for availability of hyphenation data.

`character`  

The suggested hyphen character to insert. Pass `NULL` if you do not need this information.

## Return Value

An index in the string where it is appropriate to insert a hyphen, if one exists; otherwise, `kCFNotFound`.

## See Also

### Working With Hyphenation

func CFStringIsHyphenationAvailableForLocale(CFLocale!) -> Bool

Returns a Boolean value that indicates whether hyphenation data is available.

