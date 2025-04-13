

- Core Animation
- CAPropertyAnimation
-  valueFunction 

Instance Property

# valueFunction

An optional value function that is applied to interpolated values.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.1+macOS 10.5+tvOS 9.0+visionOS 1.0+

``` source
var valueFunction: CAValueFunction? { get set }
```

## Discussion

If the `valueFunction` property is not `nil`, the function is applied to the values interpolated by the animation as they are applied to the presentation layer. Defaults to `nil`.

## See Also

### Property Value Calculation Behavior

var isCumulative: Bool

Determines if the value of the property is the value at the end of the previous repeat cycle, plus the value of the current repeat cycle.

var isAdditive: Bool

Determines if the value specified by the animation is added to the current render tree value to produce the new render tree value.

