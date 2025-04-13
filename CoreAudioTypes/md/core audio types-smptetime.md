

- Core Audio Types
-  SMPTETime 

Structure

# SMPTETime

A structure that defines an SMPTE time value.

iOS 2.0+iPadOS 2.0+macOS 10.0+tvOS 9.0+visionOS 1.0+watchOS 3.0+

``` source
struct SMPTETime
```

## Overview

SMPTE (Society of Motion Picture and Television Engineers, pronounced “SIMPtee”) times are used to correlate a point in an audio stream with an external event. For example, a SMPTE time can be used to correlate a sound in an audio file with a video frame in a movie file.

Note that the frames referred to by this structure are video frames, where a video frame is a single complete image. (Compare with the definition of audio frames in the discussion for AudioStreamBasicDescription.)

A complete SMPTE time description takes 80 bits, including 32 user bits that contain vendor-specific information. The actual time-code portion of the SMPTE time description is normally sent in several messages, each message containing a portion of the time code. (The user bits are sent in a separate message.) Typically, the SMPTE time description is divided up into 8 1-byte messages, with the first nibble of each message specifying which portion of the time code is contained in the message and the second nibble containing the time information. Four such messages are normally sent with each video frame.

Video data contains somewhere from 24 to 60 frames per second (as specified by the SMPTE time type—see `SMPTE Timecode Types`) and each video frame has an associated SMPTE time. SMPTE time is based on a 24-hour clock. Each frame’s SMPTE time consists of an hour, minute, and second value, plus the number of the frame within the second. Because audio data is sampled at a much higher rate (MP3 data is sampled at over 100,000 bits per second, for example), it is frequently desirable to correlate the audio data with a time within the persistence period of a single video frame. For this reason, the time period during which a single video frame is displayed is subdivided into subframes (typically 80 or 100 subframes per frame, as specified by the `mSubFrameDivisor` field). The `mSubFrames` field specifies the number of subframes into the video frame represented by this time structure.

## Topics

### Initializers

init()

init(mSubframes: Int16, mSubframeDivisor: Int16, mCounter: UInt32, mType: SMPTETimeType, mFlags: SMPTETimeFlags, mHours: Int16, mMinutes: Int16, mSeconds: Int16, mFrames: Int16)

### Instance Properties

var mCounter: UInt32

The total number of messages received. It takes 8 messages to carry a full SMPTE time code.

var mFlags: SMPTETimeFlags

A set of flags that indicate the SMPTE state (see `SMPTE Time Flags`).

var mFrames: Int16

The value of the frames portion of the SMPTE time.

var mHours: Int16

The value of the hours portion of the SMPTE time.

var mMinutes: Int16

The value of the minutes portion of the SMPTE time.

var mSeconds: Int16

The value of the seconds portion of the SMPTE time.

var mSubframeDivisor: Int16

The number of subframes per video frame (typically 80).

var mSubframes: Int16

A subframe offset to the HH:MM:SS:FF time. You can use this field to position a time marker somewhere within the time span represented by a video frame, if necessary.

var mType: SMPTETimeType

A SMPTE time type constant indicating the kind of SMPTE time used (see `SMPTE Timecode Types`).

## Relationships

### Conforms To

- BitwiseCopyable
- Sendable

## See Also

### SMPTE Time

struct SMPTETimeFlags

A structure that defines SMPTE time flags.

enum SMPTETimeType

Constants that define SMPTE time types.

