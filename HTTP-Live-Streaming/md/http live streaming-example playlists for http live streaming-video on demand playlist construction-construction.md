

- HTTP Live Streaming
- Example playlists for HTTP Live Streaming
-  Video on Demand playlist construction 

Article

# Video on Demand playlist construction

Understand the basic composition for a Video on Demand playlist.

## Overview

For Video on Demand (VOD) sessions, media files are available representing the entire duration of the presentation. The index file is static and contains a complete list of URLs to all media files created since the beginning of the presentation. This kind of session allows the client full access to the entire program.

### Example

This code is an example of a Video on Demand playlist:

```
#EXTM3U
#EXT-X-PLAYLIST-TYPE:VOD
#EXT-X-TARGETDURATION:10
#EXT-X-VERSION:4
#EXT-X-MEDIA-SEQUENCE:0
#EXTINF:10.0,
http://example.com/movie1/fileSequenceA.ts
#EXTINF:10.0,
http://example.com/movie1/fileSequenceB.ts
#EXTINF:10.0,
http://example.com/movie1/fileSequenceC.ts
#EXTINF:9.0,
http://example.com/movie1/fileSequenceD.ts
#EXT-X-ENDLIST
```

These are the tags used in the Video on Demand playlist example:

**EXTM3U:** Indicates that the playlist is an extended M3U file. This type of file is distinguished from a basic `M3U` file by changing the tag on the first line to `EXTM3U`. All HLS playlists must start with this tag.

**EXT-X-PLAYLIST-TYPE:** Provides mutability information that applies to the entire playlist file. This tag may contain a value of either `EVENT` or `VOD`. If the tag is present and has a value of `EVENT`, the server must not change or delete any part of the playlist file (although it may append lines to it). If the tag is present and has a value of `VOD`, the playlist file must not change.

**EXT-X-TARGETDURATION:** Specifies the maximum media-file duration.

**EXT-X-VERSION:** Indicates the compatibility version of the playlist file. The playlist media and its server must comply with all provisions of the most recent version of the IETF Internet-Draft of the HTTP Live Streaming specification that defines that protocol version.

**EXT-X-MEDIA-SEQUENCE:** Indicates the sequence number of the first URL that appears in a playlist file. Each media file URL in a playlist has a unique integer sequence number. The sequence number of a URL is higher by 1 than the sequence number of the URL that preceded it. The media sequence numbers have no relation to the names of the files.

**EXTINF:** A record marker that describes the media file identified by the URL that follows it. Each media file URL must be preceded by an `EXTINF` tag. This tag contains a duration attribute that’s an integer or floating-point number in decimal positional notation that specifies the duration of the media segment in seconds. This value must be less than or equal to the target duration.

Important

Always use floating-point `EXTINF` durations (supported in protocol version 3). This allows the client to minimize round-off errors when seeking within the stream.

**EXT-X-ENDLIST:** Indicates that no more media files will be added to the playlist file.

The VOD playlist example above uses full pathnames for the media file playlist entries. While this is allowed, using relative pathnames is preferable. Relative pathnames are more portable than absolute pathnames and are relative to the URL of the playlist file. Using full pathnames for the individual playlist entries often results in more text than using relative pathnames. Here’s the same playlist with relative pathnames:

```
#EXTM3U
#EXT-X-PLAYLIST-TYPE:VOD
#EXT-X-TARGETDURATION:10
#EXT-X-VERSION:4
#EXT-X-MEDIA-SEQUENCE:0
#EXTINF:10.0,
fileSequenceA.ts
#EXTINF:10.0,
fileSequenceB.ts
#EXTINF:10.0,
fileSequenceC.ts
#EXTINF:9.0,
fileSequenceD.ts
#EXT-X-ENDLIST
```

## See Also

### Basic playlists

Live Playlist (sliding window) construction

Understand the basic composition for a live session playlist.

Event playlist construction

Learn about the basic composition of an event session playlist.

Creating a Multivariant Playlist

Offer multiple playlist files to provide different encodings of the same content.

