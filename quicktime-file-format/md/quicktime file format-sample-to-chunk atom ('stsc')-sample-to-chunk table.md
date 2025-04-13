

- QuickTime File Format
- Sample-to-chunk atom ('stsc')
-  Sample-to-chunk table 

Data field

# Sample-to-chunk table

A table that maps samples to chunks.

## Overview

The following table shows the structure of an entry in a sample-to-chunk table. Each sample-to-chunk atom contains such a table, which identifies the chunk for each sample in a media. Each entry in the table contains a first chunk field, a samples per chunk field, and a sample description ID field. From this information, you can ascertain where samples reside in the media data.

The layout of a sample-to-chunk table entry is as follows.

| Fields                | Bytes |
|-----------------------|-------|
| First chunk           | 4     |
| Samples per chunk     | 4     |
| Sample description ID | 4     |

You define a sample-to-chunk table entry by specifying the following data elements.

First chunk  
The first chunk number using this table entry.

Samples per chunk  
The number of samples in each chunk.

Sample description ID  
The identification number associated with the sample description for the sample. For details on sample description atoms, see Sample description atom ('stsd').

An example of a sample-to-chunk table is as follows.

| First chunk | Samples per chunk | Sample description ID |
|-------------|-------------------|-----------------------|
| 1           | 3                 | 23                    |
| 3           | 1                 | 23                    |
| 5           | 1                 | 24                    |

Each table entry corresponds to a set of consecutive chunks, each of which contains the same number of samples. Furthermore, each of the samples in these chunks must use the same sample description. Whenever the number of samples per chunk or the sample description changes, you must create a new table entry. If all the chunks have the same number of samples per chunk and use the same sample description, this table has one entry.

## See Also

### Data fields

Size

A 32-bit integer that specifies the number of bytes in this sample-to-chunk atom.

Type

A 32-bit integer that identifies the atom type.

Version

A 1-byte specification of the version of this sample-to-chunk atom.

Flags

A 3-byte space for sample-to-chunk flags.

Number of entries

A 32-bit integer containing the count of entries in the sample-to-chunk table.

