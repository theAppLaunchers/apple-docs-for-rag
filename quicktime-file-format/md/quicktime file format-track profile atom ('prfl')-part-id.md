

- QuickTime File Format
- Track profile atom ('prfl')
-  Part-ID 

Data field

# Part-ID

A 32-bit field that defines the feature as being either brand-specific or universal.

## Overview

The second field is the part-ID, which defines the feature as being either brand-specific or universal. Brand-specific features are particular to a specific brand. Universal features can be found in any file type that uses the profile atom. Universal features have a part-ID of four ASCII spaces (`0x20202020`). Brand-specific features have a part-ID that is one of the compatible brand codes for that file type, as specified in the file type atom (`'ftyp'`). For example, the part-ID for QuickTime-specific features is `'qt '`. All features described in this documentation, however, are universal.

## See Also

### Data fields

Reserved

A 32-bit field.

Feature code

A 32-bit unsigned integer that represents a code specifying a feature.

Value

A 32-bit field that represents a value related to a feature.

