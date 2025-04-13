

- Swift
- Duration
- Duration.TimeFormatStyle
- Duration.TimeFormatStyle.Pattern
-  hourMinute(padHourToLength:roundSeconds:) 

Type Method

# hourMinute(padHourToLength:roundSeconds:)

Returns a pattern to format a duration with hours and minutes only, with the given unit configurations.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+watchOS 9.0+

``` source
static func hourMinute(
    padHourToLength: Int,
    roundSeconds: FloatingPointRoundingRule = .toNearestOrEven
) -> Duration.TimeFormatStyle.Pattern
```

## Parameters 

`padHourToLength`  

Padding for the hour field. For example, setting this value to `2` formats one hour as `01:00` in the `en_US` locale.

`roundSeconds`  

The rule to use for rounding the minutes value, given the remaining seconds value. Use one of the cases from the FloatingPointRoundingRule enumeration.

## Return Value

A Duration.TimeFormatStyle.Pattern that formats a duration with hours and minutes only, using the given unit configurations.

## See Also

### Creating a pattern

static func hourMinuteSecond(padHourToLength: Int, fractionalSecondsLength: Int, roundFractionalSeconds: FloatingPointRoundingRule) -> Duration.TimeFormatStyle.Pattern

Returns a pattern to format a duration with hours, minutes, and seconds, with the given unit configurations.

static func minuteSecond(padMinuteToLength: Int, fractionalSecondsLength: Int, roundFractionalSeconds: FloatingPointRoundingRule) -> Duration.TimeFormatStyle.Pattern

Returns a pattern to format a duration with minutes and seconds only, with the given unit configurations.

