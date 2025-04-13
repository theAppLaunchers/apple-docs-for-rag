

- QuickTime File Format
- Media header atom ('mdhd')
-  Type 

Data field

# Type

A 32-bit integer that identifies the atom type.

## Overview

This field must be set to `'mdhd'`.

## See Also

### Data fields

Size

A 32-bit integer that specifies the number of bytes in this media header atom.

Version

One byte that specifies the version of this header atom.

Flags

Three bytes of space for media header flags.

Creation time

A 32-bit integer that specifies the creation date for the media atom.

Modification time

A 32-bit integer that specifies the last modification date for the media atom.

Time scale

A time value that indicates the time scale for this media.

Duration

The duration of this media in units of its time scale.

Language

A 16-bit integer that specifies the language code for this media.

Quality

A 16-bit integer that specifies the media’s playback quality.

