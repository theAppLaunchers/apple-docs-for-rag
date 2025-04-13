

- Video Toolbox
-  VTDecompressionSessionCopyBlackPixelBuffer(\_:pixelBufferOut:) 

Function

# VTDecompressionSessionCopyBlackPixelBuffer(\_:pixelBufferOut:)

Copies a black pixel buffer from the decompression session.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.1+macOS 10.8+tvOS 10.2+visionOS 1.0+

``` source
func VTDecompressionSessionCopyBlackPixelBuffer(
    _ session: VTDecompressionSession,
    pixelBufferOut: UnsafeMutablePointer
) -> OSStatus
```

## Parameters 

`session`  

The decompression session.

`pixelBufferOut`  

A pointer to receive the copied pixel buffer.

## Return Value

An `OSStatus` value that indicates the result of the operation.

## Discussion

The pixel buffer is in the same format as the decompression session.

## See Also

### Decoding Frames

func VTDecompressionSessionCanAcceptFormatDescription(VTDecompressionSession, formatDescription: CMFormatDescription) -> Bool

Indicates whether the session can decode frames with the given format description.

func VTDecompressionSessionDecodeFrame(VTDecompressionSession, sampleBuffer: CMSampleBuffer, flags: VTDecodeFrameFlags, frameRefcon: UnsafeMutableRawPointer?, infoFlagsOut: UnsafeMutablePointer&lt;VTDecodeInfoFlags>?) -> OSStatus

Decompresses a video frame.

func VTDecompressionSessionDecodeFrame(VTDecompressionSession, sampleBuffer: CMSampleBuffer, flags: VTDecodeFrameFlags, infoFlagsOut: UnsafeMutablePointer&lt;VTDecodeInfoFlags>?, outputHandler: VTDecompressionOutputHandler) -> OSStatus

Decompresses a video frame and invokes the output callback when the decompression completes.

func VTDecompressionSessionDecodeFrame(VTDecompressionSession, sampleBuffer: CMSampleBuffer, flags: VTDecodeFrameFlags, infoFlagsOut: UnsafeMutablePointer&lt;VTDecodeInfoFlags>?, completionHandler: (OSStatus, VTDecodeInfoFlags, CVImageBuffer?, [CMTaggedBuffer]?, CMTime, CMTime) -> Void) -> OSStatus

Decompresses a video frame and calls the provided output closure when decompression completes.

func VTDecompressionSessionFinishDelayedFrames(VTDecompressionSession) -> OSStatus

Directs the decompression session to emit all delayed frames.

func VTDecompressionSessionWaitForAsynchronousFrames(VTDecompressionSession) -> OSStatus

Waits for any and all outstanding asynchronous and delayed frames to complete, then returns.

