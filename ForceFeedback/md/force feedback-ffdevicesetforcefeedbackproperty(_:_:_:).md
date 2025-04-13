

- Force Feedback
-  FFDeviceSetForceFeedbackProperty(\_:\_:\_:) 

Function

# FFDeviceSetForceFeedbackProperty(\_:\_:\_:)

Retrieves the device’s force feedback capabilities.

Mac Catalyst 13.0+macOS 10.2+

``` source
func FFDeviceSetForceFeedbackProperty(
    _ deviceReference: FFDeviceObjectReference!,
    _ property: FFProperty,
    _ pValue: UnsafeMutableRawPointer!
) -> HRESULT
```

## Parameters 

`deviceReference`  

An opaque reference handle to the device object that is be disposed of. This handle is obtained from a previous call to FFCreateDevice.

`property`  

The following property values are defined for a FF device:

FFPROP_AUTOCENTER

Specifies whether the actuated FF axes are self-centering. This property controls the device’s “default centering spring”.

The pValue member points to a UInt32 can be one of the following values.

0 - OFF: The device should not automatically center when the user releases the device. An application that uses force feedback should disable autocentering before playing effects.

1 - ON: The device should automatically center when the user releases the device.

Not all devices support the autocenter property.

FFPROP_FFGAIN

Sets the gain for the device.

The pValue member points to a UInt32 that contains a gain value that is applied to all effects created on the device. The value is an integer in the range from 0 through 10,000, specifying the amount by which effect magnitudes should be scaled for the device. For example, a value of 10,000 indicates that all effect magnitudes are to be taken at face value. A value of 9,000 indicates that all effect magnitudes are to be reduced to 90% of their nominal magnitudes.

Setting a gain value is useful when an application wants to scale down the strength of all force feedback effects uniformly, based on user preferences.

`pValue`  

Address of the location where the property value is to be read. SetForceFeedbackProperty will assume that the data is valid, and of the correct type.

## Return Value

If the method succeeds, the return value is FF_OK or FFERR_UNSUPPORTED. If the method fails, the return value can be one of the following error values:

## Discussion

FFERR_INVALIDPARAM

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

func FFEffectDownload(FFEffectObjectReference!) -> HRESULT

Places the effect on the device. If the effect is already on the device, the existing effect is updated to match the values set by the FFEffectSetParameters method.

func FFEffectEscape(FFEffectObjectReference!, UnsafeMutablePointer&lt;FFEFFESCAPE>!) -> HRESULT

Sends a hardware-specific command to the driver.

func FFEffectGetEffectStatus(FFEffectObjectReference!, UnsafeMutablePointer&lt;FFEffectStatusFlag>!) -> HRESULT

Sends a hardware-specific command to the driver.

func FFEffectGetParameters(FFEffectObjectReference!, UnsafeMutablePointer&lt;FFEFFECT>!, FFEffectParameterFlag) -> HRESULT

Retrieves information about an effect.

func FFEffectSetParameters(FFEffectObjectReference!, UnsafeMutablePointer&lt;FFEFFECT>!, FFEffectParameterFlag) -> HRESULT

Sets the characteristics of an effect.

func FFEffectStart(FFEffectObjectReference!, UInt32, FFEffectStartFlag) -> HRESULT

Begins playing an effect. If the effect is already playing, it is restarted from the beginning. If the effect has not been downloaded or has been modified since its last download, it is downloaded before being started. This default behavior can be suppressed by passing the FFES_NODOWNLOAD flag.

