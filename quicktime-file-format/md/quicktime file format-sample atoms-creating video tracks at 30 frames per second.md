

- QuickTime File Format
- Sample atoms
-  Creating video tracks at 30 frames per second 

Article

# Creating video tracks at 30 frames per second

Configure your time-to-sample atom for 30 frames per second.

## Overview

The duration of a video frame is stored in the time-to-sample atom contained within a sample table atom. This duration cannot be interpreted without the media’s time scale, which defines the units-per-second for the duration. In this example, each frame has the same duration, so the time-to-sample atom has one entry, which applies to all video frames in the media.

As long as the ratio between frame duration and media time scale remains `1:30`, any combination of values can be used for the duration and time scale. The larger the time scale the shorter the maximum duration. Since a movie defaults to a time scale of `600`, this is a good number to use. It is also the least common multiple for `24`, `25`, and `30`, making it handy for much of the math you are likely to encounter when making a movie.

The movie time scale is independent of the media time scale. Since you want to avoid movie edits that don’t land on frame boundaries, it is a good idea to keep the movie time scale and the media time scale the same, or to make the movie time scale an even multiple of the media time scale. The movie time scale is stored in the movie header atom.

With a time scale of `600` in the media header atom, the time-to-sample atom would contain the data values listed in following table.

| Field             | Value    |
|-------------------|----------|
| Atom size         | `24`     |
| Atom type         | `'stts'` |
| Version/Flags     | `0`      |
| Number of entries | `1`      |
| Sample count      | `n`      |
| Sample duration   | `20`     |

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

Chunk offset atom ('stco')

An atom that identifies the location of each chunk of data in the media’s data stream.

