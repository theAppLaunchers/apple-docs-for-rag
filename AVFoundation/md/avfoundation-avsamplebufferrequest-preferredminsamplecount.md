

- AVFoundation
- AVSampleBufferRequest
-  preferredMinSampleCount 

Instance Property

# preferredMinSampleCount

The preferred minimum number of samples to load.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 10.10+tvOS 16.0+visionOS 1.0+watchOS 9.0+

``` source
var preferredMinSampleCount: Int { get set }
```

## Discussion

A value that isn’t `0` indicates the preferred number of samples to load. Fewer samples may be loaded if there is a change of format description.

## See Also

### Configuring Sample Buffer Request Parameters

var direction: AVSampleBufferRequest.Direction

The buffer sample direction.

enum Direction

The modes that describe the buffer request direction.

var limitCursor: AVSampleCursor?

The limiting position for sample loading.

var maxSampleCount: Int

The maximum number of samples to load.

var mode: AVSampleBufferRequest.Mode

The sample buffer request mode.

enum Mode

The modes in which a sample buffer generator processes a request.

var overrideTime: CMTime

The deadline for sample data and output PTS for the sample buffer.

var startCursor: AVSampleCursor

The starting cursor position.

