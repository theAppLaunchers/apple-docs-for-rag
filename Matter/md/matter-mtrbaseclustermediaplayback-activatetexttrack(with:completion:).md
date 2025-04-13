

- Matter
- MTRBaseClusterMediaPlayback
-  activateTextTrack(with:completion:) 

Instance Method

# activateTextTrack(with:completion:)

Command ActivateTextTrack

iOS 18.4+iPadOS 18.4+Mac Catalyst 18.4+macOS 15.4+tvOS 18.4+visionOS 2.4+watchOS 11.4+

``` source
func activateTextTrack(
    with params: MTRMediaPlaybackClusterActivateTextTrackParams,
    completion: @escaping MTRStatusCompletion
)
```

``` source
func activateTextTrack(with params: MTRMediaPlaybackClusterActivateTextTrackParams) async throws
```

## Discussion

Upon receipt, the server SHALL set the active Text Track to the one identified by the TrackID in the Track catalog for the streaming media. If the TrackID does not exist in the Track catalog, OR does not correspond to the streaming media OR no media is being streamed at the time of receipt of this command, the server SHALL return an error status of INVALID_ARGUMENT.

