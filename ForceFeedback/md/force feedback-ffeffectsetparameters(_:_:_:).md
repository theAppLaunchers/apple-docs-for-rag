

- Force Feedback
-  FFEffectSetParameters(\_:\_:\_:) 

Function

# FFEffectSetParameters(\_:\_:\_:)

Sets the characteristics of an effect.

Mac Catalyst 13.0+macOS 10.2+

``` source
func FFEffectSetParameters(
    _ effectReference: FFEffectObjectReference!,
    _ pFFEffect: UnsafeMutablePointer!,
    _ flags: FFEffectParameterFlag
) -> HRESULT
```

## Parameters 

`effectReference`  

An opaque reference handle to an effect object. This is obtained from a previous call to FFDeviceCreateEffect.

`pFFEffect`  

Address of a FFEFFECT structure that contains effect information. The dwSize member must be filled in by the application before calling this method, as well as any members specified by corresponding bits in the flags parameter.

`flags`  

Flags that specify which portions of the effect information are to be set and how the downloading of the parameters should be handled. The value can be 0 or one or more of the following constants:

FFEP_AXES

The cAxes and rgdwAxes members contain data.

FFEP_DIRECTION

The cAxes and rglDirection members contain data. The dwFlags member specifies (with FFEFF_CARTESIAN or FFEFF_POLAR) the coordinate system in which the values should be interpreted.

FFEP_DURATION

The dwDuration member contains data.

FFEP_ENVELOPE

The lpEnvelope member points to a FFENVELOPE structure that contains data. To detach any existing envelope from the effect, pass this flag and set the lpEnvelope member to NULL.

FFEP_GAIN

The dwGain member contains data.

FFEP_NODOWNLOAD

Suppress the automatic FFEffect_Download that is normally performed after the parameters are updated.

FFEP_NORESTART

Suppress the stopping and restarting of the effect to change parameters. See Remarks.

FFEP_SAMPLEPERIOD

The dwSamplePeriod member contains data.

FFEP_START

The effect is to be started (or restarted if it is currently playing) after the parameters are updated. By default, the play state of the effect is not altered.

FFEP_STARTDELAY

The dwStartDelay member contains data.

FFEP_TRIGGERBUTTON

The dwTriggerButton member contains data.

The dwTriggerRepeatInterval member contains data.

FFEP_TYPESPECIFICPARAMS

The lpvTypeSpecificParams and cbTypeSpecificParams members of the FFEFFECT structure contain the address and size of type-specific data for the effect.

## Return Value

If the method succeeds, the return value is FF_OK. If the method fails, the return value can be one of the following error values:

## Discussion

FFERR_INVALIDPARAM

FFERR_UNSUPPORTEDAXIS

FFERR_OUTOFMEMORY

FFERR_DEVICEPAUSED

FFERR_DEVICEFULL

FFERR_INVALIDDOWNLOADID

FFERR_INTERNAL

FFERR_EFFECTTYPEMISMATCH

## Discussion

The FFEffectSetParameters method automatically downloads the effect, but this behavior can be suppressed by setting the FFEP_NODOWNLOAD flag. If automatic download has been suppressed, you can manually download the effect by invoking the FFEffectDownload method.

If the effect is playing while the parameters are changed, the new parameters take effect as if they were the parameters when the effect started.

For example, suppose a periodic effect with a duration of three seconds is started. After two seconds, the direction of the effect is changed. The effect then continues for one additional second in the new direction. The envelope, phase, amplitude, and other parameters of the effect continue smoothly, as if the direction had not changed.

In the same situation, if after two seconds the duration of the effect were changed to 1.5 seconds, the effect would stop.

Normally, if the driver cannot update the parameters of a playing effect, the driver is permitted to stop the effect, update the parameters, and then restart the effect. Passing the FFEP_NORESTART flag suppresses this behavior. If the driver cannot update the parameters of an effect while it is playing, the error code FFERR_EFFECTPLAYING is returned, and the parameters are not updated.

No more than one of the FFEP_NODOWNLOAD, FFEP_START, and FFEP_NORESTART flags should be set. (It is also valid to pass none of them.)

These three flags control download and playback behavior as follows:

If FFEP_NODOWNLOAD is set, the effect parameters are updated but not downloaded to the device.

If the FFEP_START flag is set, the effect parameters are updated and downloaded to the device, and the effect is started just as if the FFEffect_Start method had been called with the dwIterations parameter set to 1 and with no flags. (Combining the update with FFEP_START is slightly faster than calling Start separately, because it requires less information to be transmitted to the device.)

If neither FFEP_NODOWNLOAD nor FFEP_START is set and the effect is not playing, the parameters are updated and downloaded to the device.

If neither FFEP_NODOWNLOAD nor FFEP_START is set and the effect is playing, the parameters are updated if the device supports on-the-fly updating. Otherwise the behavior depends on the state of the FFEP_NORESTART flag. If it is set, the error code FFERR_EFFECTPLAYING is returned. If it is clear, the effect is stopped, the parameters are updated, and the effect is restarted.

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

func FFEffectGetParameters(FFEffectObjectReference!, UnsafeMutablePointer&lt;FFEFFECT>!, FFEffectParameterFlag) -> HRESULT

Retrieves information about an effect.

func FFEffectStart(FFEffectObjectReference!, UInt32, FFEffectStartFlag) -> HRESULT

Begins playing an effect. If the effect is already playing, it is restarted from the beginning. If the effect has not been downloaded or has been modified since its last download, it is downloaded before being started. This default behavior can be suppressed by passing the FFES_NODOWNLOAD flag.

