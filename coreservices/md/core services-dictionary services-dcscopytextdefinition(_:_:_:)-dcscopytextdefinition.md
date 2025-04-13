

- Core Services
- Dictionary Services
-  DCSCopyTextDefinition(\_:\_:\_:) 

Function

# DCSCopyTextDefinition(\_:\_:\_:)

Returns the definition associated with the provided text range.

Mac Catalyst 13.1+macOS 10.5+

``` source
func DCSCopyTextDefinition(
    _ dictionary: DCSDictionary?,
    _ textString: CFString,
    _ range: CFRange
) -> Unmanaged?
```

## Parameters 

`dictionary`  

This parameter is reserved for future use, so pass `NULL`. Dictionary Services searches in all active dictionaries.

`textString`  

Text that contains the word or phrase to look up.

`range`  

A range that specifies the location of the word or phrase in the `textString` parameter. If text string exactly specifies the word or phrase that you want to look up, you can pass the range of the text string. For example, for the word `make`, you would pass (`0`,`4`) to specify the range.

If the `textString` parameter contains the word or phrase, but does not specify it exactly, then pass the range returned by the function DCSGetTermRangeInString(_:_:_:).

## Return Value

The definition of the word or phrase, as plain text. The returned text does not contain any elements that are marked with a `priority` attribute whose value is `2`.

## Discussion

This function returns the description of the first matching record found in the active dictionaries. It searches first in the default word definition dictionary which, in the English environment, is the Oxford dictionary.

