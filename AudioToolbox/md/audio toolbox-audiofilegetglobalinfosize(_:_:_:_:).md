

- Audio Toolbox
-  AudioFileGetGlobalInfoSize(\_:\_:\_:\_:) 

Function

# AudioFileGetGlobalInfoSize(\_:\_:\_:\_:)

Gets the size of a global audio file property.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.1+macOS 10.3+tvOS 9.0+visionOS 1.0+

``` source
func AudioFileGetGlobalInfoSize(
    _ inPropertyID: AudioFilePropertyID,
    _ inSpecifierSize: UInt32,
    _ inSpecifier: UnsafeMutableRawPointer?,
    _ outDataSize: UnsafeMutablePointer
) -> OSStatus
```

## Parameters 

`inPropertyID`  

The property whose data size you want to get. For possible values, see Audio File Global Info Properties.

`inSpecifierSize`  

The size of the specifier data.

`inSpecifier`  

A pointer to a *specifier* (a pointer to a buffer containing some data which is different for each property. The type of the data required is described in the description of each property.)

`outDataSize`  

A pointer to the size in bytes of the current value of the property. To get the size of the property value, you need a buffer of this size.

## Return Value

A result code. See Result Codes.

## Discussion

This function can be used to get information about the capabilities of Audio File Service data types, for example, to determine which file types can take which data formats.

## See Also

### Working with Global Information

func AudioFileGetGlobalInfo(AudioFilePropertyID, UInt32, UnsafeMutableRawPointer?, UnsafeMutablePointer&lt;UInt32>, UnsafeMutableRawPointer) -> OSStatus

Copies the value of a global property into a buffer.

