

- Core Services
- Carbon Core
- Unicode Utilities
-  UCKeySequenceDataIndex 

Structure

# UCKeySequenceDataIndex

Contains offsets to a list of character sequences for a `'uchr'` resource.

Mac Catalyst 13.0+macOS 10.0+

``` source
struct UCKeySequenceDataIndex
```

## Overview

The Unicode keyboard-layout ( `'uchr'`) resource contains the data necessary to map virtual key codes to Unicode character codes for a given keyboard layout. The `'uchr'` format consists of a header information section and five key mapping data sections. The `UCKeySequenceDataIndex` type is used in the fifth key mapping section of the `'uchr'` resource.

The `UCKeySequenceDataIndex` structure contains offsets to a list of character sequences for the `'uchr'` resource. This permits a single keypress to generate a sequence of characters, or to generate a single character outside the range that can be represented directly by values of type UCKeyOutput or UCKeyCharSeq.

## Topics

### Initializers

init()

init(keySequenceDataIndexFormat: UInt16, charSequenceCount: UInt16, charSequenceOffsets: UInt16)

### Instance Properties

var charSequenceCount: UInt16

An unsigned 16-bit integer specifying the number of Unicode character sequences that follow the end of the `UCKeySequenceDataIndex` structure.

var charSequenceOffsets: UInt16

An array of offsets from the beginning of the `UCKeySequenceDataIndex` structure to the Unicode character sequences that follow it. Because a given offset indicates both the beginning of a new character sequence and the end of the sequence that precedes it, the length of each sequence is determined by the difference between the offset to that sequence and the value of the next offset in the array. The array contains one more entry than the number of character sequences; the final entry is the offset to the end of the final character sequence.

var keySequenceDataIndexFormat: UInt16

An unsigned 16-bit integer identifying the format of the `UCKeySequenceDataIndex` structure. Set to `kUCKeySequenceDataIndexFormat`.

