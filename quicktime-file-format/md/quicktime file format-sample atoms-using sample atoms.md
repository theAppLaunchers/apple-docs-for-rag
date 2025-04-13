

- QuickTime File Format
- Sample atoms
-  Using sample atoms 

Article

# Using sample atoms

Find samples or key frames in sample atoms.

## Overview

This section presents examples using the atoms just described. These examples are intended to help you understand the relationships between these atoms.

The first section, Finding a sample, describes the steps that the video media handler uses to find the sample that contains the media data for a particular time in a media. The second section, Finding a key frame, describes the steps that the video media handler uses to find an appropriate key frame for a specific time in a movie.

## Finding a sample

When QuickTime displays a movie or track, it directs the appropriate media handler to access the media data for a particular time. The media handler must correctly interpret the data stream to retrieve the requested data. In the case of video media, the media handler traverses several atoms to find the location and size of a sample for a given media time.

The media handler performs the following steps:

1.  Determines the time in the media time coordinate system.

2.  Examines the time-to-sample atom to determine the sample number that contains the data for the specified time.

3.  Scans the sample-to-chunk atom to discover which chunk contains the sample in question.

4.  Extracts the offset to the chunk from the chunk offset atom.

5.  Finds the offset within the chunk and the sample’s size by using the sample size atom.

## Finding a key frame

Finding a key frame for a specified time in a movie is slightly more complicated than finding a sample for a specified time. The media handler must use the sync sample atom and the time-to-sample atom together in order to find a key frame.

The media handler performs the following steps:

1.  Examines the time-to-sample atom to determine the sample number that contains the data for the specified time.

2.  Scans the sync sample atom to find the key frame that precedes the sample number chosen in step 1.

3.  Scans the sample-to-chunk atom to discover which chunk contains the key frame.

4.  Extracts the offset to the chunk from the chunk offset atom.

5.  Finds the offset within the chunk and the sample’s size by using the sample size atom.

## See Also

### Describing samples

Sample table atom ('stbl')

An atom that contains information for converting from media time to sample number to sample location.

Seeking with a QuickTime file

Seek with a QuickTime file using child atoms.

Sample description atom ('stsd')

An atom that stores information that allows you to decode samples in the media.

Time-to-sample atom ('stts')

An atom that stores duration information for a media’s samples, providing a mapping from a time in a media to the corresponding data sample.

Creating video tracks at 30 frames per second

Configure your time-to-sample atom for 30 frames per second.

Creating video tracks at 29.97 frames per second

Configure your time-to-sample atom for 29.97 frames per second.

Creating sound tracks at 44.1 kHz

Configure your time-to-sample atom for sound at 44.1 kHz.

Composition offset atom ('ctts')

An atom you use to specify out-of-order video samples.

Composition shift least greatest atom ('cslg')

An atom that summarizes the calculated minimum and maximum offsets between decode and composition time, as well as the start and end times, for all samples.

Using composition offset and composition shift least greatest atoms

Calculate the offset shift when you store an out of order video stream’s sample table.

Sync sample atom ('stss')

An atom that identifies the key frames in the media.

Partial sync sample atom ('stps')

An atom that lists the partial sync samples.

Sample-to-chunk atom ('stsc')

An atom that stores chunk information for the samples in a media.

Referencing two data files with a single track

Use multiple sample descriptions reference data in multiple files for a track.

Sample size atom ('stsz')

An atom you use to specify the size of each sample in the media.

