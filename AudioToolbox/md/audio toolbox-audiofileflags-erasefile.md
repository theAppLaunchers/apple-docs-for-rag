

- Audio Toolbox
- AudioFileFlags
-  eraseFile 

Type Property

# eraseFile

iOSiPadOSMac CatalystmacOStvOSvisionOS

``` source
static var eraseFile: AudioFileFlags { get }
```

## Discussion

If set, the AudioFileCreateWithURL(_:_:_:_:_:) function erases the contents of an existing file. If not set, then the function fails if the file already exists.

## See Also

### Flags

static var dontPageAlignAudioData: AudioFileFlags

Typically, the audio data in a file is page aligned. To make reading the file data as fast as possible, you can use page-aligned data to take advantage of optimized code paths in the file system. However, when space is at a premium, you might want to avoid the additional padding required to attain alignment. To do so, set this flag when calling AudioFileCreate or AudioFileCreateWithURL(_:_:_:_:_:).

