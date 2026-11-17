- SwiftUI
- View
- onChange(of:initial:_:)

Instance Method

# onChange(of:initial:_:)

Adds a modifier for this view that fires an action when a specific value changes.

iOS 17.0+ iPadOS 17.0+ Mac Catalyst 17.0+ macOS 14.0+ tvOS 17.0+ visionOS 1.0+ watchOS 10.0+

```swift
nonisolated
func onChange<V>(
    of value: V,
    initial: Bool = false,
    _ action: @escaping () -> Void
) -> some View where V : Equatable
```

```swift
nonisolated
func onChange<V>(
    of value: V,
    initial: Bool = false,
    _ action: @escaping (V, V) -> Void
) -> some View where V : Equatable
```

## Parameters

value

The value to check against when determining whether to run the closure.

initial

Whether the action should be run when this view initially appears.

action

A closure to run when the value changes.

oldValue

The old value that failed the comparison check (or the initial value when requested).

newValue

The new value that failed the comparison check.

## Return Value

A view that fires an action when the specified value changes.

## Discussion

...

## See also

...