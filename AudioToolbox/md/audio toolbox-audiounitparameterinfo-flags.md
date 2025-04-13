

- Audio Toolbox
- AudioUnitParameterInfo
-  flags 

Instance Property

# flags

The host should check for this flag and, if present, release the parameter name when it is finished with it.

iOSiPadOSMac CatalystmacOStvOSvisionOS

``` source
var flags: AudioUnitParameterOptions
```

## Discussion

Due to some vagaries about the ways in which Parameter’s CFNames have been described, it was necessary to add a flag: flag_CFNameRelease. In normal usage a parameter name is essentially a static object, but sometimes an audio unit will generate parameter names dynamically. As these are expected to be doc://com.apple.documentation/documentation/corefoundation/cfstring-rfh objects, in that case the host should release those names when it is finished with them, but there was no way to communicate this distinction in behavior. Thus, if an audio unit can generate a name dynamically, it should set this flag in the parameter’s info. The host should check for this flag and, if present, release the parameter name when it is finished with it.

