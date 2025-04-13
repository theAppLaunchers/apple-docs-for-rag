

- Foundation
- NSDate
-  distantFuture 

Type Property

# distantFuture

A date object representing a date in the distant future.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.0+macOS 10.0+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
class var distantFuture: Date { get }
```

## Return Value

An NSDate object representing a date in the distant future (in terms of centuries).

## Discussion

You can pass this value when an NSDate object is required to have the date argument essentially ignored. For example, the NSWindow method nextEvent(matching:until:inMode:dequeue:) returns `nil` if an event specified in the event mask does not happen before the specified date. You can use the object returned by distantFuture as the date argument to wait indefinitely for the event to occur.

```
myEvent = [myWindow nextEventMatchingMask:myEventMask
    untilDate:[NSDate distantFuture]
    inMode:NSDefaultRunLoopMode
    dequeue:YES];
```

## See Also

### Getting Temporal Boundaries

class var distantPast: Date

A date object representing a date in the distant past.

