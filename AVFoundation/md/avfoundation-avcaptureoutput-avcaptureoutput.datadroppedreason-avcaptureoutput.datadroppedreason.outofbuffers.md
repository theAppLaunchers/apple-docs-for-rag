

- AVFoundation
- AVCaptureOutput
- AVCaptureOutput.DataDroppedReason
-  AVCaptureOutput.DataDroppedReason.outOfBuffers 

Case

# AVCaptureOutput.DataDroppedReason.outOfBuffers

The system dropped data because the capture output exhausted its internal pool of memory buffers.

iOS 11.0+iPadOS 11.0+Mac Catalyst 14.0+macOS 10.15+tvOS 17.0+visionOS 1.0+

``` source
case outOfBuffers
```

## Discussion

This situation typically indicates that your delegate object is holding on to captured data buffers for too long. If you need to perform extended processing of captured data, copy that data into buffers whose lifetimes you manage instead of relying on buffers vended by the capture output.

## See Also

### Reasons

case none

The system didn’t drop data.

case lateData

The system dropped data because you’ve configured capture output to drop data when delegate queue is in a blocked state, and there’s data to deliver.

case discontinuity

The system dropped data because the device providing data experienced a discontinuity, and the output lost an unknown number of data objects.

