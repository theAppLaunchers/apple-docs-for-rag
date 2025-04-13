

- QuickTime File Format
- Media data atom types
-  Music media 

Article

# Music media

Store note-based audio data, such as MIDI data, in QuickTime movies.

## Overview

Music media is used to store note-based audio data, such as MIDI data, in QuickTime movies. It has a media type of `'musi'`.

## Music sample description

The music sample description uses the standard sample description header, as described in Sample description atom ('stsd').

The data format field in the sample description is always set to `'musi'`. The music media handler adds an additional 32-bit integer field to the sample description containing flags. Currently no flags are defined, and this field should be set to `0`.

Following the flags field, there may be appended data in the QuickTime music format. This data consists of part-to-instrument mappings in the form of General events containing note requests. One note request event should be present for each part that will be used in the sample data.

## Music Sample Data

The sample data for music samples consists entirely of data in the QuickTime music format. Typically, up to 30 seconds of notes are grouped into a single sample.

## See Also

### Video and sound

Video media

Store compressed and uncompressed image data in QuickTime movies.

Sound media

Store compressed and uncompressed audio data in QuickTime movies.

MPEG-1 media

Store MPEG-1 video streams, MPEG-1, layer 2 audio streams, and multiplexed MPEG-1 audio and video streams in QuickTime movies.

Movie media

Movie media is used to encapsulate embedded movies within QuickTime movies.

Defining media data layouts

Use efficient media layouts.

