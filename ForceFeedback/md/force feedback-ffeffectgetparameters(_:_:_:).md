

- Force Feedback
-  FFEffectGetParameters(\_:\_:\_:) 

Function

# FFEffectGetParameters(\_:\_:\_:)

Retrieves information about an effect.

Mac Catalyst 13.0+macOS 10.2+

``` source
func FFEffectGetParameters(
    _ effectReference: FFEffectObjectReference!,
    _ pFFEffect: UnsafeMutablePointer!,
    _ flags: FFEffectParameterFlag
) -> HRESULT
```

## Parameters 

`effectReference`  

An opaque reference handle to an effect object. This is obtained from a previous call to FFDeviceCreateEffect.

`pFFEffect`  

Address of a FFEFFECT structure that receives effect information. The dwSize member must be filled in by the application before calling this method.

`flags`  

Flags that specify which parts of the effect information are to be retrieved. The value can be 0 or one or more of the following constants:

FFEP_ALLPARAMS

The union of all other FFEP\_\* flags, indicating that all members of the FFEFFECT structure are being requested.

FFEP_AXES

The cAxes and rgdwAxes members should receive data. The cAxes member on entry contains the size (in DWORDs) of the buffer pointed to by the rgdwAxes member. If the buffer is too small, the method returns FFERR_MOREDATA and sets cAxes to the necessary size of the buffer.

FFEP_DIRECTION

The cAxes and rglDirection members should receive data. The cAxes member on entry contains the size (in DWORDs) of the buffer pointed to by the rglDirection member. If the buffer is too small, the GetParameters method returns FFERR_MOREDATA and sets cAxes to the necessary size of the buffer.

The dwFlags member must include at least one of the coordinate system flags (FFEFF_CARTESIAN, FFEFF_POLAR, or FFEFF_SPHERICAL). The API returns the direction of the effect in one of the coordinate systems you specified, converting between coordinate systems as necessary. On exit, exactly one of the coordinate system flags is set in the dwFlags member, indicating which coordinate system the FF API used. In particular, passing all three coordinate system flags retrieves the coordinates in exactly the same format in which they were set.

FFEP_DURATION

The dwDuration member should receive data.

FFEP_ENVELOPE

The lpEnvelope member points to a FFENVELOPE structure that should receive data. If the effect does not have an envelope associated with it, the lpEnvelope member is set to NULL.

FFEP_GAIN

The dwGain member should receive data.

FFEP_SAMPLEPERIOD

The dwSamplePeriod member should receive data.

FFEP_STARTDELAY

The dwStartDelay member should receive data.

FFEP_TRIGGERBUTTON

The dwTriggerButton member should receive data.

FFEP_TRIGGERREPEATINTERVAL

The dwTriggerRepeatInterval member should receive data.

FFEP_TYPESPECIFICPARAMS

The lpvTypeSpecificParams member points to a buffer whose size is specified by the cbTypeSpecificParams member. On return, the buffer is filled in with the type-specific data associated with the effect, and the cbTypeSpecificParams member contains the number of bytes copied. If the buffer supplied by the application is too small to contain all the type-specific data, the method returns FFERR_MOREDATA, and the cbTypeSpecificParams member contains the required size of the buffer in bytes.

## Return Value

If the method succeeds, the return value is FF_OK. If the method fails, the return value can be one of the following error values:

## Discussion

FFERR_INVALIDPARAM

FFERR_NOTDOWNLOADED

FFERR_MOREDATA

## Discussion

Common errors resulting in a FFERR_INVALIDPARAM error include not setting the dwSize member of the FFEFFECT structure, passing invalid flags, or not setting up the members in the FFEFFECT structure properly in preparation for receiving the effect information.

## See Also

### Miscellaneous

func FFCreateDevice(io_service_t, UnsafeMutablePointer&lt;FFDeviceObjectReference?>!) -> HRESULT

Creates a new API device object from an OS object in preparation to use the device for force feedback.

func FFDeviceCreateEffect(FFDeviceObjectReference!, CFUUID!, UnsafeMutablePointer&lt;FFEFFECT>!, UnsafeMutablePointer&lt;FFEffectObjectReference?>!) -> HRESULT

Creates and initializes an instance of an effect identified by the effect UUID on the device.

func FFDeviceEscape(FFDeviceObjectReference!, UnsafeMutablePointer&lt;FFEFFESCAPE>!) -> HRESULT

Sends a hardware-specific command to the device.

func FFDeviceGetForceFeedbackCapabilities(FFDeviceObjectReference!, UnsafeMutablePointer&lt;FFCAPABILITIES>!) -> HRESULT

Retrieves the device’s force feedback capabilities.

func FFDeviceGetForceFeedbackProperty(FFDeviceObjectReference!, FFProperty, UnsafeMutableRawPointer!, IOByteCount) -> HRESULT

Gets properties that define the device behavior.

func FFDeviceGetForceFeedbackState(FFDeviceObjectReference!, UnsafeMutablePointer&lt;FFState>!) -> HRESULT

Retrieves the state of the device’s force feedback system.

func FFDeviceReleaseEffect(FFDeviceObjectReference!, FFEffectObjectReference!) -> HRESULT

Disposes of an API effect object created with FFDeviceCreateEffect.

func FFDeviceSendForceFeedbackCommand(FFDeviceObjectReference!, FFCommandFlag) -> HRESULT

Sends a command to the device’s force feedback system.

func FFDeviceSetCooperativeLevel(FFDeviceObjectReference!, UnsafeMutableRawPointer!, FFCooperativeLevelFlag) -> HRESULT

Function is unimplemented in version 1.0 of this API

func FFDeviceSetForceFeedbackProperty(FFDeviceObjectReference!, FFProperty, UnsafeMutableRawPointer!) -> HRESULT

Retrieves the device’s force feedback capabilities.

func FFEffectDownload(FFEffectObjectReference!) -> HRESULT

Places the effect on the device. If the effect is already on the device, the existing effect is updated to match the values set by the FFEffectSetParameters method.

func FFEffectEscape(FFEffectObjectReference!, UnsafeMutablePointer&lt;FFEFFESCAPE>!) -> HRESULT

Sends a hardware-specific command to the driver.

func FFEffectGetEffectStatus(FFEffectObjectReference!, UnsafeMutablePointer&lt;FFEffectStatusFlag>!) -> HRESULT

Sends a hardware-specific command to the driver.

func FFEffectSetParameters(FFEffectObjectReference!, UnsafeMutablePointer&lt;FFEFFECT>!, FFEffectParameterFlag) -> HRESULT

Sets the characteristics of an effect.

func FFEffectStart(FFEffectObjectReference!, UInt32, FFEffectStartFlag) -> HRESULT

Begins playing an effect. If the effect is already playing, it is restarted from the beginning. If the effect has not been downloaded or has been modified since its last download, it is downloaded before being started. This default behavior can be suppressed by passing the FFES_NODOWNLOAD flag.

