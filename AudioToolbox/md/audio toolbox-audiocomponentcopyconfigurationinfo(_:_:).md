

- Audio Toolbox
-  AudioComponentCopyConfigurationInfo(\_:\_:) 

Function

# AudioComponentCopyConfigurationInfo(\_:\_:)

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 10.7+visionOS 1.0+

``` source
func AudioComponentCopyConfigurationInfo(
    _ inComponent: AudioComponent,
    _ outConfigurationInfo: UnsafeMutablePointer?>
) -> OSStatus
```

## See Also

### Getting Information About a Component

func AudioComponentInstanceCanDo(AudioComponentInstance, Int16) -> Bool

Determines if an audio component instance implements a particular function.

func AudioComponentGetDescription(AudioComponent, UnsafeMutablePointer&lt;AudioComponentDescription>) -> OSStatus

Gets the class description, as an `AudioComponentDescription` structure, of an audio component.

func AudioComponentCopyName(AudioComponent, UnsafeMutablePointer&lt;Unmanaged&lt;CFString>?>) -> OSStatus

Returns the generic name of an audio component.

func AudioComponentGetVersion(AudioComponent, UnsafeMutablePointer&lt;UInt32>) -> OSStatus

Gets the version of an audio component in hexadecimal form as `0xMMMMmmDD` (major, minor, dot).

func AudioComponentCopyIcon(AudioComponent) -> UIImage?

struct AudioComponentPlugInInterface

typealias AudioComponentMethod

