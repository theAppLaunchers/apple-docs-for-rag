

- Cinematic
- CNScript
-  primaryDecision(at:) 

Instance Method

# primaryDecision(at:)

The primary decision that’s in effect at the specified time, unless it’s outside the time range of the Cinematic script.

iOS 17.0+iPadOS 17.0+macOS 14.0+tvOS 17.0+

``` source
final func primaryDecision(at time: CMTime) -> CNDecision?
```

## Parameters 

`time`  

The time of interest.

## Return Value

A value representing the primary decision that’s in effect at the specified time, unless it’s outside the time range of the Cinematic script. The value also represents the decision being transitioned away from the given time is during a focus transition.

