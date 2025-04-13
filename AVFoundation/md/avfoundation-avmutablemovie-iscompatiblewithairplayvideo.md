

- AVFoundation
- AVMutableMovie
-  isCompatibleWithAirPlayVideo 

Instance Property

# isCompatibleWithAirPlayVideo

A Boolean value that indicates whether the asset is compatible with AirPlay Video.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+macOS 10.11+visionOS 1.0+

``` source
var isCompatibleWithAirPlayVideo: Bool { get }
```

## Discussion

This property value is true if you can play this composition’s content to an external AirPlay device, like an Apple TV.

## See Also

### Determining Suitability

var isPlayable: Bool

A Boolean value that indicates whether the asset has playable content.

var isReadable: Bool

A Boolean value that indicates whether you can extract the asset’s media data using an asset reader.

var isExportable: Bool

A Boolean value that indicates whether you can export this asset using an export session.

var isComposable: Bool

A Boolean value that indicates whether you can use the asset as a segment of a composition track.

var isCompatibleWithSavedPhotosAlbum: Bool

A Boolean value that indicates whether you can write the composition to the Saved Photos album.

