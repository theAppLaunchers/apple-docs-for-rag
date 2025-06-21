Framework

# AlarmKit

Schedule prominent alarms and countdowns to help people manage their time.

iOS 26.0+BetaiPadOS 26.0+BetaMac Catalyst 26.0+Beta

## [Overview](/documentation/AlarmKit#Overview)

Use `AlarmKit` to create custom alarms and timers in your app. `AlarmKit` provides a framework for managing alarms with customizable schedules and UI. It supports one-time and repeating alarms, with the option for countdown durations and snooze functionality. `AlarmKit` handles alarm authorization and provides UI for both templated and widget presentations. It supports traditional alarms, timers, or both, and provides methods to schedule, pause, resume, and cancel alarms.

## [Topics](/documentation/AlarmKit#topics)

### [Alarm management](/documentation/AlarmKit#Alarm-management)

[

Scheduling an alarm with AlarmKit](/documentation/alarmkit/scheduling-an-alarm-with-alarmkit)

Create prominent alerts at specified dates for your iOS app.

```swift
```swift
```swift
class AlarmManager
```
```

An object that exposes functions to work with alarms: scheduling, snoozing, cancelling.
```
```swift
```swift
```swift
struct Alarm
```
```

An object that describes an alarm that can alert once or on a repeating schedule.
```

### [Buttons](/documentation/AlarmKit#Buttons)

```swift
```swift
```swift
```swift
struct AlarmButton
```
```

A structure that defines the appearance of buttons.
```
```

### [Views](/documentation/AlarmKit#Views)

```swift
```swift
```swift
```swift
struct AlarmPresentation
```
```

An object that describes the content required for the alarm UI.
```
```swift
```swift
```swift
struct AlarmPresentationState
```
```

An object that describes the mutable content of the alarm.
```
```swift
```swift
```swift
struct AlarmAttributes
```
```

An object that contains all information necessary for the alarm UI.
```
```swift
```swift
```swift
protocol AlarmMetadata
```
```

A metadata object that contains information about an alarm.
```
```

Beta Software

This documentation contains preliminary information about an API or technology in development. This information is subject to change, and software implemented according to this documentation should be tested with final operating system software.

[Learn more about using Apple's beta software](https://developer.apple.com/support/beta-software/)