

- Swift Charts
- LinePlot
-  init(x:y:t:domain:function:) 

Initializer

# init(x:y:t:domain:function:)

Creates a mark that graphs a parametric function (x, y) = f(t).

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+tvOS 18.0+visionOS 2.0+watchOS 11.0+

``` source
nonisolated
init(
    x: Text,
    y: Text,
    t: Text,
    domain: ClosedRange,
    function: @escaping (Double) -> (x: Double, y: Double)
)
```

Available when `Content` is `FunctionLinePlotContent`.

## Discussion

Parameters:

- x: The localized string key for the x label.

- y: The localized string key for the y label.

- t: The localized string key for the t label.

- domain: The domain of t. Must be a finite domain.

- function: The function to graph. Returns a tuple of (x, y) for a value of t.

Note

For t values where the function is undefined or is infinity, the function is expected to return `Double.nan` or `Double.infinity` respectively.

