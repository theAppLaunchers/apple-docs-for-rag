

- QuickTime File Format
- Deprecated atoms
- Appendix F: Profile atom guidelines
- Universal features
-  Maximum video size in a track 

Article

# Maximum video size in a track

## Overview

Containing profile atom  
Track (video), movie

`part-ID`  
`0x20202020` (universal feature)

`feature-code`  
`'tvsz'`

`feature-value`  
A 32-bit packed structure holding width and height of the largest picture buffer needed for a video track.

## Feature Values

A packed structure in a 32-bit value:

```
struct {
    unsigned integer(16) width;
    unsigned integer(16) height;
};
```

In big-endian order, the top 16 bits correspond to the width. The lower 16 bits correspond to the height.

## Writer Responsibilities

A writer of the Maximum Track Video Size feature should record a value that is equal to or greater than the largest height and width of any sample description in the video track. This does not include the effect of any scaling or offset applied by the track matrix and may not be the same as the track height and track width.

A writer (such as a CE device) may choose to record a constant size based upon its current recording mode even if the actual size recorded in the track is smaller.

## Feature Value Algorithm

Examine all sample descriptions for the track, and use the maximum width and maximum height found in any sample. The maximum width and maximum height may come from independent sample descriptions.

## Reader Responsibilities

A reader of this feature code should compare the recorded value with its own image buffer limits.

The reader should not interpret the value of this feature as the current video size. To determine the current video size, the reader should use the dimensions of all currently displaying video tracks, their matrices, and the movie matrix.

## Comments

The width and height correspond to the largest image buffer dimensions needed for a visual track. When present in a movie-level profile, these atoms document the maximum video size found in each of the movie’s tracks.

The summarized width and height do not take into account any scaling or translation caused by the track or movie matrices, and are not necessarily the same as the track height and width.

For the case where there is a single video track with an identity track and matrix and an identity movie matrix, the movie’s maximum video size feature would have the same value as the track’s feature.

Warning

Use of the “clean aperture” sample description extension does not affect the value of the track visual size, as the picture buffer is needed immediately after decoding, prior to any clean aperture clipping.

## See Also

### Setting features

Table of features

Maximum video bit rate

Average video bit rate

Maximum audio bit rate

Average audio bit rate

QuickTime video codec type

QuickTime audio codec type

MPEG-4 video profile

MPEG-4 video codec

MPEG-4 video object type

MPEG-4 audio codec

Maximum video size in a movie

Maximum video frame rate in a single track

Average video frame rate in a single track

Video variable frame rate indication

