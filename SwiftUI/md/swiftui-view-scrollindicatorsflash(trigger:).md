

- SwiftUI
- View
-  scrollIndicatorsFlash(trigger:) 

Instance Method

# scrollIndicatorsFlash(trigger:)

Flashes the scroll indicators of scrollable views when a value changes.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+tvOS 17.0+visionOS 1.0+watchOS 10.0+

``` source
nonisolated
func scrollIndicatorsFlash(trigger value: some Equatable) -> some View
```

## Parameters 

`value`  

The value that causes scroll indicators to flash. The value must conform to the Equatable protocol.

## Return Value

A view that flashes any visible scroll indicators when a value changes.

## Discussion

When the value that you provide to this modifier changes, the scroll indicators of any scrollable views within the modified view hierarchy briefly flash. The following example configures the scroll indicators to flash any time `flashCount` changes:

```
@State private var isPresented = false
@State private var flashCount = 0

ScrollView {
    // ...
}
.scrollIndicatorsFlash(trigger: flashCount)
.sheet(isPresented: $isPresented) {
    // ...
}
.onChange(of: isPresented) { newValue in
    if newValue {
        flashCount += 1
    }
}
```

Only scroll indicators that you configure to be visible flash. To flash scroll indicators when a scroll view initially appears, use scrollIndicatorsFlash(onAppear:) instead.

## See Also

### Showing scroll indicators

func scrollIndicatorsFlash(onAppear: Bool) -> some View

Flashes the scroll indicators of a scrollable view when it appears.

func scrollIndicators(ScrollIndicatorVisibility, axes: Axis.Set) -> some View

Sets the visibility of scroll indicators within this view.

var horizontalScrollIndicatorVisibility: ScrollIndicatorVisibility

The visibility to apply to scroll indicators of any horizontally scrollable content.

var verticalScrollIndicatorVisibility: ScrollIndicatorVisibility

The visiblity to apply to scroll indicators of any vertically scrollable content.

struct ScrollIndicatorVisibility

The visibility of scroll indicators of a UI element.

