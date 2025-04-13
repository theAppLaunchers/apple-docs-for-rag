

- DeviceActivity
- DeviceActivityReport
-  accessibilityInputLabels(\_:isEnabled:) 

Instance Method

# accessibilityInputLabels(\_:isEnabled:)

Sets alternate input labels with which users identify a view.

DeviceActivitySwiftUIiOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+tvOS 18.0+visionOS 2.0+watchOS 11.0+

``` source
nonisolated
func accessibilityInputLabels(
    _ inputLabels: [S],
    isEnabled: Bool
) -> ModifiedContent where S : StringProtocol
```

## Parameters 

`inputLabels`  

The accessibility input labels to apply.

`isEnabled`  

If true the accessibility input labels are applied; otherwise the accessibility input labels are unchanged.

## Discussion

Provide labels in descending order of importance. Voice Control and Full Keyboard Access use the input labels.

Note

If you don’t specify any input labels, the user can still refer to the view using the accessibility label that you add with the `accessibilityLabel()` modifier.

