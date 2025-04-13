

- Core Foundation
-  CFStringFind(\_:\_:\_:) 

Function

# CFStringFind(\_:\_:\_:)

Searches for a substring within a string and, if it is found, yields the range of the substring within the object’s characters.

iOSiPadOSMac CatalystmacOStvOSvisionOSwatchOS

``` source
func CFStringFind(
    _ theString: CFString!,
    _ stringToFind: CFString!,
    _ compareOptions: CFStringCompareFlags
) -> CFRange
```

## Parameters 

`theString`  

The string in which to search for `stringToFind`.

`stringToFind`  

The string to search for in `theString`.

`compareOptions`  

Flags that select different types of comparisons, such as localized comparison, case-insensitive comparison, and non-literal comparison. If you want the default comparison behavior, pass `0`. See String Comparison Flags for the available flags.

## Return Value

The range of the located substring within `theString`. If a match is not located, the returned CFRange structure will have a location of kCFNotFound and a length of `0` (either of which is enough to indicate failure).

## Discussion

This function is a convenience when you want to know if the entire range of characters represented by a string contains a particular substring. If you want to search only part of the characters of a string, use the CFStringFindWithOptions(_:_:_:_:_:) function. Both of these functions return upon finding the first occurrence of the substring, so if you want to find out about multiple occurrences, call the CFStringCreateArrayWithFindResults(_:_:_:_:_:) function.

Depending on the comparison-option flags specified, the length of the resulting range might be different than the length of the search string.

## See Also

### Searching Strings

func CFStringCreateArrayWithFindResults(CFAllocator!, CFString!, CFString!, CFRange, CFStringCompareFlags) -> CFArray!

Searches a string for multiple occurrences of a substring and creates an array of ranges identifying the locations of these substrings within the target string.

func CFStringFindCharacterFromSet(CFString!, CFCharacterSet!, CFRange, CFStringCompareFlags, UnsafeMutablePointer&lt;CFRange>!) -> Bool

Query the range of the first character contained in the specified character set.

func CFStringFindWithOptions(CFString!, CFString!, CFRange, CFStringCompareFlags, UnsafeMutablePointer&lt;CFRange>!) -> Bool

Searches for a substring within a range of the characters represented by a string and, if the substring is found, returns its range within the object’s characters.

func CFStringFindWithOptionsAndLocale(CFString!, CFString!, CFRange, CFStringCompareFlags, CFLocale!, UnsafeMutablePointer&lt;CFRange>!) -> Bool

Returns a Boolean value that indicates whether a given string was found in a given source string.

func CFStringGetLineBounds(CFString!, CFRange, UnsafeMutablePointer&lt;CFIndex>!, UnsafeMutablePointer&lt;CFIndex>!, UnsafeMutablePointer&lt;CFIndex>!)

Given a range of characters in a string, obtains the line bounds—that is, the indexes of the first character and the final characters of the lines containing the range.

