

- AVFoundation
- AVCaptureAudioFileOutput
-  audioSettings 

Instance Property

# audioSettings

The settings used to decode or re-encode audio before it is output by the receiver.

macOS 10.7+

``` source
var audioSettings: [String : Any]? { get set }
```

## Discussion

The value of this property is a dictionary containing values for audio settings keys defined in `AVAudioSettings.h`. If you set the value of this property to `nil`, the output vends samples in their device native format.

## See Also

### Configuring Output

var metadata: [AVMetadataItem]

A collection of metadata to be written to the receiver’s output files.

