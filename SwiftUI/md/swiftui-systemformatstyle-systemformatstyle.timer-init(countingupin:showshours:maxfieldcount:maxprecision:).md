

- SwiftUI
- SystemFormatStyle
- SystemFormatStyle.Timer
-  init(countingUpIn:showsHours:maxFieldCount:maxPrecision:) 

Initializer

# init(countingUpIn:showsHours:maxFieldCount:maxPrecision:)

Create a timer format style that counts up to the given interval.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+tvOS 18.0+visionOS 2.0+watchOS 11.0+

``` source
init(
    countingUpIn interval: Range,
    showsHours: Bool = true,
    maxFieldCount: Int = 3,
    maxPrecision: Duration = .seconds(1)
)
```

## Discussion

A timer styled display that counts from zero up to the given `timerInterval`.

- interval: The interval during which the timer counts up.

- showsHours: If true, the timer shows the hours as a separate element on the formatted string, as long as the duration is at least one hour. If false, the timer displays minute values greather than sixty.

- maxFieldCount: The number of fields that can be shown at once. For example, 1 hour, 34 minutes is shown as `1:34:00` by default, but as `1:34` if the `maxFieldCount` is set to two. The style automatically excludes more significant fields if their value is zero and they are not necessary for the format pattern, making room for less significant fields.

- maxPrecision: The precision at which the input is formatted. E.g. by default, seconds are shown, making the maximum precision one second. Setting the maximum precision to `.seconds(60)` would only allow hours and minutes to be shown.

