Framework

# RelevanceKit

Provide on-device intelligence with contextual clues that increase your widget’s visibility on Apple Watch.

iOS 26.0+BetaiPadOS 26.0+BetaMac Catalyst 26.0+BetamacOS 26.0+BetavisionOS 26.0+BetawatchOS 26.0+Beta

## [Overview](/documentation/RelevanceKit#overview)

On Apple Watch, widgets appear in the Smart Stack in an order that best fits a person’s context. To order the widgets that appear in the Smart Stack, watchOS attempts to determine a widget’s relevance based on several factors, including contextual clues your app provides to the system.

To give your widget additional visibility in the watchOS Smart Stack and ensure it appears when a person needs it, use RelevanceKit to provide contextual clues that signal the widget’s relevance to the system. For example, your widget might be most useful at a specific location or time, or every time a person starts a workout.

Note that you use RelevanceKit in combination with [WidgetKit](/documentation/WidgetKit) and [App Intents](/documentation/AppIntents) to provide interactive and contextually relevant widgets in the Smart Stack, including iPhone widgets that appear on Apple Watch. When you add an import statement for App Intents to your code, App Intents implicitly adds a dependence to RelevanceKit . You don’t need to explicitly add `import RelevanceKit` to your code.

For more information, refer to [Increasing the visibility of widgets in Smart Stacks](/documentation/WidgetKit/Widget-Suggestions-In-Smart-Stacks).

Note

Smart Stacks are available in iOS, iPadOS, and watchOS. However, functionality provided by RelevanceKit is only available in watchOS. Calling its API on other platforms doesn’t have any effect.

## [Topics](/documentation/RelevanceKit#topics)

### [Providing relevance information](/documentation/RelevanceKit#Providing-relevance-information)

[

Increasing the visibility of widgets in Smart Stacks](/documentation/WidgetKit/Widget-Suggestions-In-Smart-Stacks)

Provide contextual information and donate intents to the system to make sure your widget appears prominently in Smart Stacks.

```swift
```swift
```swift
struct RelevantContext
```
```

A type that specifies conditions for relevance.
```

### [Fitness clues](/documentation/RelevanceKit#Fitness-clues)

[`static func fitness(RelevantContext.FitnessCondition) -> RelevantContext`](/documentation/relevancekit/relevantcontext/fitness\(_:\))

Tells the system a widget is relevant because of a person’s fitness activity.

```swift
```swift
```swift
struct FitnessCondition
```
```

Values that represent a person’s fitness activity.
```

### [Hardware clues](/documentation/RelevanceKit#Hardware-clues)

[`static func hardware(headphones: RelevantContext.HeadphonesCondition) -> RelevantContext`](/documentation/relevancekit/relevantcontext/hardware\(headphones:\))

Tells the system a widget is relevant when a person’s headphones are connected.

```swift
```swift
```swift
struct HeadphonesCondition
```
```

A structure that indicates whether a person’s headphones are connected.
```

### [Location clues](/documentation/RelevanceKit#Location-clues)

[`static func location(CLRegion) -> RelevantContext`](/documentation/relevancekit/relevantcontext/location\(_:\))

Tells the system a widget is relevant at a specific location.

[`static func location(inferred: RelevantContext.InferredLocation) -> RelevantContext`](/documentation/relevancekit/relevantcontext/location\(inferred:\))

Tells the system a widget is relevant at a person’s inferred location.

```swift
```swift
```swift
struct InferredLocation
```
```

A structure with values for a person’s inferred home, work, school, and commute locations.
```

### [Sleep clues](/documentation/RelevanceKit#Sleep-clues)

[`static func sleep(RelevantContext.SleepCondition) -> RelevantContext`](/documentation/relevancekit/relevantcontext/sleep\(_:\))

Tells the system a widget is relevant because of a person’s sleep schedule.

```swift
```swift
```swift
struct SleepCondition
```
```

Values that represent a person’s typical bedtime or wakeup time.
```

### [Time clues](/documentation/RelevanceKit#Time-clues)

[`static func date(Date) -> RelevantContext`](/documentation/relevancekit/relevantcontext/date\(_:\))

Tells the system a widget is relevant at a specific date.

[`static func date(Date, kind: RelevantContext.DateKind) -> RelevantContext`](/documentation/relevancekit/relevantcontext/date\(_:kind:\))

Tells the system a widget is relevant at a specific date and provides an additional contextual hint.

[`static func date(interval: DateInterval, kind: RelevantContext.DateKind) -> RelevantContext`](/documentation/relevancekit/relevantcontext/date\(interval:kind:\))

An exact range in time: similar uses as `date()`, but with a known endpoint, such as a calendar event.

[`static func date(range: ClosedRange<Date>, kind: RelevantContext.DateKind) -> RelevantContext`](/documentation/relevancekit/relevantcontext/date\(range:kind:\))

An exact range in time: similar uses as `date()`, but with a known endpoint, such as a calendar event.

```swift
```swift
```swift
struct DateKind
```
```

Values the system uses as additional context for time-based relevance clues.
```

[`static func date(from: Date, to: Date) -> RelevantContext`](/documentation/relevancekit/relevantcontext/date\(from:to:\))

An exact range in time: similar uses as `date()`, but with a known endpoint.

Deprecated

Beta Software

This documentation contains preliminary information about an API or technology in development. This information is subject to change, and software implemented according to this documentation should be tested with final operating system software.

[Learn more about using Apple's beta software](https://developer.apple.com/support/beta-software/)