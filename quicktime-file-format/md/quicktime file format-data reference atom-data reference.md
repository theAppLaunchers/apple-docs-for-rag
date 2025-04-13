

- QuickTime File Format
- Data reference atom
-  Data reference 

Data field

# Data reference

A data reference to a QuickTime movie, or to a stream or file that QuickTime can play.

## Overview

If the reference type is `'alis'` this field contains the contents of an `AliasHandle`. If the reference type is `'url '` this field contains a NULL-terminated string that can be interpreted as a URL. The URL can be absolute or relative, and can specify any protocol that QuickTime supports, including `http://`, `ftp://`, `rtsp://`, `file:///`, and `data:`.

## See Also

### Data fields

Size

The number of bytes in this data reference atom.

Type

The type of this atom.

Flags

A 32-bit integer containing flags.

Data reference type

The data reference type.

Data reference size

The size of the data reference in bytes, expressed as a 32-bit integer.

