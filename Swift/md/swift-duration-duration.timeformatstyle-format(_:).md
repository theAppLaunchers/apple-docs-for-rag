

- Swift
- Duration
- Duration.TimeFormatStyle
-  format(\_:) 

Instance Method

# format(\_:)

Creates a locale-aware string representation from a duration value.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+watchOS 9.0+

``` source
func format(_ value: Duration) -> String
```

## Parameters 

`value`  

The duration value to format.

## Return Value

A string representation of the duration, according to the style’s pattern and locale.

## Discussion

Use this method when you want to create a format style and repeatedly use it to format different durations. For one-off cases with default formatting, call the formatted(_:) method of Duration instead.

