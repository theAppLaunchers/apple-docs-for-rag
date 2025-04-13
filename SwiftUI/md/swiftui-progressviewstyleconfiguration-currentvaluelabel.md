

- SwiftUI
- ProgressViewStyleConfiguration
-  currentValueLabel 

Instance Property

# currentValueLabel

A view that describes the current value of a progress view.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+macOS 11.0+tvOS 14.0+visionOS 1.0+watchOS 7.0+

``` source
var currentValueLabel: ProgressViewStyleConfiguration.CurrentValueLabel?
```

## Discussion

If `nil`, then the value of the progress view is either self-evident from the surrounding context or unknown, and the style does not need to provide any additional description.

If the progress view is defined using a `Progress` instance, then this label is equivalent to its `localizedAdditionalDescription`.

## See Also

### Configuring the current value label

struct CurrentValueLabel

A type-erased label that describes the current value of a progress view.

