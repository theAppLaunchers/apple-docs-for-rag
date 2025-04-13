

- AVFoundation
- AVSampleCursor
-  step(byDecodeTime:wasPinned:) 

Instance Method

# step(byDecodeTime:wasPinned:)

Moves the cursor by a given delta time on the decode timeline.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 10.10+tvOS 16.0+visionOS 1.0+watchOS 9.0+

``` source
func step(
    byDecodeTime deltaDecodeTime: CMTime,
    wasPinned outWasPinned: UnsafeMutablePointer?
) -> CMTime
```

## Parameters 

`deltaDecodeTime`  

The amount of time to move in the decode timeline.

`outWasPinned`  

The system sets the value of this pointer to true if the cursor reaches the beginning or the end of the sample sequence before it reaches the requested time. You may specify `nil` if you’re not interested in this information.

## Return Value

The amount of time the cursor was moved along the decode timeline. Because sample cursors snap to sample boundaries when stepped, this value may not be equal to the specified time delta even if the cursor wasn’t pinned.

## See Also

### Navigating Samples

func step(byPresentationTime: CMTime, wasPinned: UnsafeMutablePointer&lt;ObjCBool>?) -> CMTime

Moves the cursor by a given delta time on the presentation timeline.

func stepInDecodeOrder(byCount: Int64) -> Int64

Moves the cursor a given number of samples in decode order.

func stepInPresentationOrder(byCount: Int64) -> Int64

Moves the cursor a given number of samples in presentation order.

