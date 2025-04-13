

- QuickTime File Format
-  Track reference type atom 

Atom

# Track reference type atom

An atom that defines relationships with tracks of a specific type.

## Mentioned in 

QuickTime File Format change log

## Overview

Each track reference atom defines relationships with tracks of a specific type. The reference type implies a track type. The track reference types and their descriptions are as follows.

| Reference Type | Description |
|----|----|
| `'cdsc'` | The track reference is contained in a timed metadata track (see Timed metadata media for more detail) and provides links to the tracks for which it contains descriptive characteristics. Note: If the timed metadata track describes characteristics of the entire movie, there will be no track reference of type `‘cdsc’` between it and another track. |
| `'chap'` | Chapter or scene list. Usually references a text track. |
| `'clcp'` | Closed caption. In any track, this identifies a closed captioning track that contains text that is appropriate for the referring track. See Closed captioning media for more information. |
| `'fall'` | In a sound track, this references a track in a different format but with identical content, if one exists; for example, an AC3 track might reference an AAC track with identical content. See Alternate sound tracks in Preparing sound and subtitle alternate groups for use with Apple devices. |
| `'folw'` | In a sound track, this references a subtitle track that is to be used as the sound track’s default subtitle track. If the subtitle track is part of a subtitle track pair, this should reference the the forced subtitle track of the pair. This is needed only if language tagging cannot be used. See Relationships across alternate groups in Preparing sound and subtitle alternate groups for use with Apple devices. |
| `'forc'` | Forced subtitle track. In the regular track of a subtitle track pair, this references the forced track. See Subtitle Sample Data for more information. |
| `'hint'` | The referenced tracks contain the original media for this hint track. |
| `'scpt'` | Transcript. Usually references a text track. |
| `'ssrc'` | Non-primary source. Indicates that the referenced track should send its data to this track, rather than presenting it. The referencing track will use the data to modify how it presents its data. See Track input map atoms for more information. |
| `'sync'` | Synchronization. Usually between a video and sound track. Indicates that the two tracks are synchronized. The reference can be from either track to the other, or there may be two references. |
| `'tmcd'` | Time code. Usually references a time code track. |

You can determine the number of track references stored in a track reference type atom by subtracting its header size from its overall size and then dividing by the size, in bytes, of a track ID.

## Topics

### Data fields

Size

A 32-bit integer that specifies the number of bytes in this track reference type atom.

Type

A 32-bit integer that identifies the atom type.

Track IDs

A list of track ID values (32-bit integers) specifying the related tracks.

## See Also

### Atoms for track references

Track reference atom ('tref')

An atom that defines relationships between tracks.

