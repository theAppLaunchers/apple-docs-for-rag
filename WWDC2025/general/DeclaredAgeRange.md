Framework

# Declared Age Range

Create age-appropriate experiences in your app by asking people to share their age range.

iOS 26.0+BetaiPadOS 26.0+BetaMac Catalyst 26.0+BetamacOS 26.0+Beta

## [Overview](/documentation/DeclaredAgeRange#Overview)

Use the Declared Age Range framework to request people to share their age range with your app. For children in a Family Sharing group, a Family Organizer can decide whether to always share a child’s age information with your app, ask the child every time, or never share their age information. Along with an age range, the system returns an [`AgeRangeService.AgeRangeDeclaration`](/documentation/declaredagerange/agerangeservice/agerangedeclaration) for the age range a person provides.

## [Topics](/documentation/DeclaredAgeRange#topics)

### [Essentials](/documentation/DeclaredAgeRange#Essentials)

[`com.apple.developer.declared-age-range`](/documentation/BundleResources/Entitlements/com.apple.developer.declared-age-range)

A Boolean value indicating whether your app may request a person’s age range.

### [Age range requests](/documentation/DeclaredAgeRange#Age-range-requests)

```swift
```swift
```swift
```swift
struct AgeRangeService
```
```

A request for the age range of a person logged onto iCloud on the device.
```
```swift
```swift
```swift
struct DeclaredAgeRangeAction
```
```

Provides an action to request a person’s declared age range.
```
```

Beta Software

This documentation contains preliminary information about an API or technology in development. This information is subject to change, and software implemented according to this documentation should be tested with final operating system software.

[Learn more about using Apple's beta software](https://developer.apple.com/support/beta-software/)