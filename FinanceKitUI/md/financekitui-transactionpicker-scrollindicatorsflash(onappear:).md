

- FinanceKitUI
- TransactionPicker
-  scrollIndicatorsFlash(onAppear:) 

Instance Method

# scrollIndicatorsFlash(onAppear:)

Flashes the scroll indicators of a scrollable view when it appears.

FinanceKitUISwiftUIiOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+tvOS 17.0+watchOS 10.0+

``` source
nonisolated
func scrollIndicatorsFlash(onAppear: Bool) -> some View
```

## Parameters 

`onAppear`  

A Boolean value that indicates whether the scroll indicators flash when the scroll view appears.

## Return Value

A view that flashes any visible scroll indicators when it first appears.

## Discussion

Use this modifier to control whether the scroll indicators of a scroll view briefly flash when the view first appears. For example, you can make the indicators flash by setting the `onAppear` parameter to `true`:

```
ScrollView {
    // ...
}
.scrollIndicatorsFlash(onAppear: true)
```

Only scroll indicators that you configure to be visible flash. To flash scroll indicators when a value changes, use `View/scrollIndicatorsFlash(trigger:)` instead.

