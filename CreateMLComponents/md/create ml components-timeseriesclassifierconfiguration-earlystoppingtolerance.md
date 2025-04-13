

- Create ML Components
- TimeSeriesClassifierConfiguration
-  earlyStoppingTolerance 

Instance Property

# earlyStoppingTolerance

The early-stopping tolerance.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+tvOS 18.0+visionOS 2.0+

``` source
var earlyStoppingTolerance: Float
```

## Discussion

The tolerance is used by the `fitted` method to decide when progress is no longer being made, in which case the training process will stop before the specified maximum number of iterations (known as early stopping). Significant progress happens when the validation loss decreases by at least the tolerance.

Defaults to 0.01.

Note

Early stopping only happens when using the `fitted` method with validation data.

