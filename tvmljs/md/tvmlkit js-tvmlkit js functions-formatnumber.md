

- TVMLKit JS
- TVMLKit JS Functions
-  formatNumber 

Function

# formatNumber

Formats the specified number into the given format.

tvOS 9.0+

``` source
String formatNumber(
    in int number, 
    in String styleValue, 
    in String positiveNumberFormat, 
    in String negativeNumberFormat
);
```

## Parameters 

`number`  

An integer that is the number to be formatted.

`styleValue`  

A string that designates the style the number is formatted in to. Valid values are `noStyle`, `currency`, `decimal`, `percent`, `scientific`, `spellOut`. If no value is given for this parameter, it defaults to `noStyle`.

`positiveNumberFormat`  

The formatting used for a positive number value input.

`negativeNumberFormat`  

The formatting used for a negative number value input.

## Return Value

A string containing the formatted number.

## Discussion

This function changes an integer into a string, based on the formatting styles specified. For example, `formatNumber(-60, “”, “+”, “-”)` returns “-60”.

## See Also

### Formatting Information

formatDate

Formats the given date into the given format.

formatDuration

Formats the given duration into the standard tvOS format.

