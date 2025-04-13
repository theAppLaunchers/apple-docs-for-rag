

- SwiftUI
- UnitCurve
-  velocity(at:) 

Instance Method

# velocity(at:)

Returns the rate of change (first derivative) of the output value of the curve at the given time.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+tvOS 17.0+visionOS 1.0+watchOS 10.0+

``` source
func velocity(at progress: Double) -> Double
```

## Parameters 

`progress`  

The input progress (x component). The provided value is clamped to the range \[0,1\].

## Return Value

The velocity of the output value (y component) of the curve at the given time.

## See Also

### Getting curve characteristics

func value(at: Double) -> Double

Returns the output value (y component) of the curve at the given time.

