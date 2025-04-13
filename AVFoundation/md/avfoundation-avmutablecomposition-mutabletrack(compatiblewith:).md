

- AVFoundation
- AVMutableComposition
-  mutableTrack(compatibleWith:) 

Instance Method

# mutableTrack(compatibleWith:)

Returns a composition track into which you can insert any time range of the specified asset track.

iOSiPadOSMac CatalystmacOStvOSvisionOSwatchOS

``` source
func mutableTrack(compatibleWith track: AVAssetTrack) -> AVMutableCompositionTrack?
```

## Parameters 

`track`  

The asset track to find a composition track for.

## Return Value

A mutable composition track, of `nil` if a compatible track isn’t available.

## Discussion

To optimize performance, limit the number of tracks to only what you need to present media data in parallel. To present media data of the same type serially, even from multiple assets, use a single track of that media type. You use this method to identify a suitable existing target track for an insertion.

If there’s no compatible track available, you can create a new track of the same media type as `track` using addMutableTrack(withMediaType:preferredTrackID:).

This method is the counterpart to compatibleTrack(for:) on AVAsset.

## See Also

### Managing Composition Tracks

func addMutableTrack(withMediaType: AVMediaType, preferredTrackID: CMPersistentTrackID) -> AVMutableCompositionTrack?

Adds an empty track to a composition.

func removeTrack(AVCompositionTrack)

Removes a specified track from the composition.

