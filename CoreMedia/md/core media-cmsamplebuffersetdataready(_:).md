

- Core Media
-  CMSampleBufferSetDataReady(\_:) 

Function

# CMSampleBufferSetDataReady(\_:)

Marks a sample buffer’s data as ready for use.

iOS 4.0+iPadOS 4.0+Mac Catalyst 13.1+macOS 10.7+tvOS 9.0+visionOS 1.0+watchOS 6.0+

``` source
func CMSampleBufferSetDataReady(_ sbuf: CMSampleBuffer) -> OSStatus
```

## Parameters 

`sbuf`  

The sample buffer being modified.

## Return Value

A result code. See Sample Buffer Error Codes.

## Discussion

There’s no way to undo this operation. The only way to get an “unready” `CMSampleBuffer` is to call `CMSampleBufferCreate` with the `dataReady` parameter set to `false`.

## See Also

### Determining Readiness

func CMSampleBufferDataIsReady(CMSampleBuffer) -> Bool

Returns a Boolean value that indicates whether the sample buffer’s data is ready for use.

func CMSampleBufferSetDataFailed(CMSampleBuffer, status: OSStatus) -> OSStatus

Marks the sample buffer’s data as failed to indicate that it won’t become ready.

func CMSampleBufferHasDataFailed(CMSampleBuffer, statusOut: UnsafeMutablePointer&lt;OSStatus>?) -> Bool

Returns a Boolean value that indicates whether the sample buffer’s data loading request failed.

func CMSampleBufferMakeDataReady(CMSampleBuffer) -> OSStatus

Makes the sample buffer’s data ready for use by invoking its callback to load the data.

func CMSampleBufferTrackDataReadiness(CMSampleBuffer, sampleBufferToTrack: CMSampleBuffer) -> OSStatus

Associates a sample buffer’s data readiness with that of another sample buffer.

