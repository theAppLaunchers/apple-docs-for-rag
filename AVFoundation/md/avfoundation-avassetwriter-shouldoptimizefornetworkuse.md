

- AVFoundation
- AVAssetWriter
-  shouldOptimizeForNetworkUse 

Instance Property

# shouldOptimizeForNetworkUse

A Boolean value that indicates whether to write the output file to make it more suitable for playback over a network.

iOS 4.1+iPadOS 4.1+Mac Catalyst 13.1+macOS 10.7+tvOS 9.0+visionOS 1.0+

``` source
var shouldOptimizeForNetworkUse: Bool { get set }
```

## Discussion

Setting this value to true writes the output file in a form that enables a player to begin playing the media after downloading only a small portion of it.

## See Also

### Configuring Output

var metadata: [AVMetadataItem]

An array of metadata items to write to the output file.

var directoryForTemporaryFiles: URL?

A directory to contain temporary files that the export process generates.

