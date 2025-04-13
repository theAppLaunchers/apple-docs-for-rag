

- QuickTime File Format
- Media data atom types
- Sound media
-  Sound sample data 

Article

# Sound sample data

Sound sample formats that QuickTime supports.

## Overview

The format of data stored in sound samples is completely dependent on the type of the compressed data stored in the sound sample description. The following sections discuss some of the formats supported by QuickTime.

### Uncompressed 8-bit sound

Eight-bit audio is stored in offset-binary encodings. If the data is in stereo, the left and right channels are interleaved.

### Uncompressed 16-bit sound

Sixteen-bit audio may be stored in two’s-complement encodings. If the data is in stereo, the left and right channels are interleaved.

### IMA, uLaw, and aLaw

- IMA 4:1

The IMA encoding scheme is based on a standard developed by the International Multimedia Association for pulse code modulation (PCM) audio compression. QuickTime uses a slight variation of the format to allow for random access. IMA is a 16-bit audio format which supports 4:1 compression. It is defined as follows:

```
kIMACompression = FOUR_CHAR_CODE('ima4'), /*IMA 4:1*/
```

- uLaw 2:1 and aLaw 2:1

The uLaw (mu-law) encoding scheme is used on North American and Japanese phone systems, and is coming into use for voice data interchange, and in PBXs, voice-mail systems, and Internet talk radio (via MIME). In uLaw encoding, 14 bits of linear sample data are reduced to 8 bits of logarithmic data.

The aLaw encoding scheme is used in Europe and the rest of the world.

The kULawCompression and the kALawCompression formats are typically found in `.au` formats.

### Floating-point formats

Both `kFloat32Format` and `kFloat64Format` are floating-point uncompressed formats. Depending upon codec-specific data associated with the sample description, the floating-point values may be in big-endian (network) or little-endian (Intel) byte order. This differs from the 16-bit formats, where there is a single format for each endian layout.

### 24- and 32-bit integer formats

Both `k24BitFormat` and `k32BitFormat` are integer uncompressed formats. Depending upon codec-specific data associated with the sample description, the floating-point values may be in big-endian (network) or little-endian (Intel) byte order.

### kMicrosoftADPCMFormat and kDVIIntelIMAFormat sound codecs

The `kMicrosoftADPCMFormat` and the `kDVIIntelIMAFormat` codec provide QuickTime interoperability with AVI and WAV files. The four-character codes used by Microsoft for their formats are numeric. To construct a QuickTime-supported codec format of this type, the Microsoft numeric ID is taken to generate a four-character code of the form `'msxx'` where *xx* takes on the numeric ID.

### kDVAudioFormat sound codec

The DV audio sound codec, `kDVAudioFormat`, decodes audio found in a DV stream. Since a DV frame contains both video and audio, this codec knows how to skip video portions of the frame and only retrieve the audio portions. Likewise, the video codec skips the audio portions and renders only the image.

### kQDesignCompression sound codec

The `kQDesignCompression` sound codec is the QDesign 1 (pre-QuickTime 4) format. Note that there is also a QDesign 2 format whose four-character code is `'QDM2'`.

### MPEG-1 layer 3 (MP3) codecs

The QuickTime MPEG layer 3 (MP3) codecs come in two particular flavors. The first (`kMPEGLayer3Format`) is used exclusively in the constant bit rate (CBR) case (pre-QuickTime 4). The other (`kFullMPEGLay3Format`) is used in both the CBR and variable bit rate (VBR) cases. Note that they are the same codec underneath.

### MPEG-4 audio

MPEG-4 audio is stored as a sound track with data format `'mp4a'` and certain additions to the sound sample description and sound track atom. Specifically:

- The compression ID is set to `-2` and redefined sample tables are used (see Redefined Sample Tables).

- The sound sample description includes an siDecompressionParam atom (see siDecompressionParam atom ('wave')). The `siDecompressionParam` atom includes:

  - An MPEG-4 elementary stream descriptor extension atom (see MPEG-4 elementary stream descriptor atom ('esds')).

  - The inclusion of a format atom is strongly recommended. See Format atom ('frma').

  - The last atom in the `siDecompressionParam` atom must be a terminator atom. See Terminator atom ('0x00000000').

- Other atoms may be present as well; unknown atoms should be ignored.

The audio data is stored as an elementary MPEG-4 audio stream, as defined in ISO/IEC specification 14496-1.

### Formats not currently in use: MACE 3:1 and 6:1

These compression formats are obsolete: MACE 3:1 and 6:1.

These are 8-bit sound codec formats, defined as follows:

```
kMACE3Compression = FOUR_CHAR_CODE('MAC3'), /*MACE 3:1*/
kMACE6Compression = FOUR_CHAR_CODE('MAC6'), /*MACE 6:1*/
```

## See Also

### Storing audio data

Sound sample descriptions

A sound sample description contains information that defines how to interpret sound media data.

Sound sample description extensions

Extend sound sample descriptions by appending other atoms.

Audio priming-handling encoder delay in AAC

Position a source audio signal in a sound track to handle encoder delay.

