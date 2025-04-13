

- QuickTime File Format
- Closed captioning sample data ('cdat')
-  Sample data 

Data field

# Sample data

An array of one or more byte pairs for data channel 1/field 1 (“CC1”) of a CEA-608 data stream, each byte pair corresponding to a video frame.

## Overview

For a CEA-608 track, the data is an array of one or more byte pairs for data channel 1/field 1 (“CC1”) of a CEA-608 data stream, each byte pair corresponding to a video frame. For details about the content, refer to the specification CEA-608-E, Line 21 Data Services, April, 2008. The durations of closed caption media samples can vary but should not be shorter than the number of byte pairs in the byte pair array. A closed caption media sample duration that is longer than the array length in video frames should treat additional durations as though null (`0`) byte pair bytes are received.

Note

The carriage of byte pairs for other elements of the source CEA-608-E frame data are not described here. If supported, other atom types and their content will be documented.

For a CEA-708 track, the data should be formatted according to the ANSI CEA-708-E specification, August, 2013.

## See Also

### Data fields

Size

A 32-bit integer that specifies the number of bytes in this closed captioning media data atom.

Type

A 32-bit integer that identifies the atom type.

