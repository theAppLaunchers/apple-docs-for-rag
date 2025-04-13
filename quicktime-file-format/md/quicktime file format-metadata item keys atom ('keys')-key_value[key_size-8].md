

- QuickTime File Format
- Metadata item keys atom ('keys')
-  Key_value\[Key_size-8\] 

Data field

# Key_value\[Key_size-8\]

An array of 8-bit integers, each containing the actual name of the metadata key.

## Overview

Keys with the `‘mdta’` namespace use a reverse DNS naming convention. For example, the location metadata coordinates use a metadata `key_value` of `‘com.apple.quicktime.location.ISO6709’`.

## See Also

### Data fields

Size

A 32-bit unsigned integer that indicates the size in bytes of the atom structure.

Type

A 32-bit unsigned integer value.

Version

One byte.

Flags

Three bytes.

Entry_count

A 32-bit integer indicating the number of key arrays to follow in this atom.

Key_size

A 32-bit integer indicating the size of the entire structure containing a key definition.

Key_namespace

A 32-bit integer defining a naming scheme used for metadata keys.

