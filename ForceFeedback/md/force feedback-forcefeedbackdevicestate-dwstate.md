

- Force Feedback
- ForceFeedbackDeviceState
-  dwState 

Instance Property

# dwState

Indicates various aspects of the device state.

Mac Catalyst 13.0+macOS 10.2+

``` source
UInt32 dwState;
```

## Discussion

Can indicate zero, one, or more of the following:

FFGFFS_EMPTY

Indicates that the force feedback device is devoid of any downloaded effects.

FFGFFS_STOPPED

Indicates that no effects are currently playing and the device is not paused.

FFGFFS_PAUSED

Indicates that playback of effects has been paused by a previous FFSFFC_PAUSE command.

FFGFFS_ACTUATORSON

Indicates that the device’s force-feedback actuators are enabled.

FFGFFS_ACTUATORSOFF

Indicates that the device’s force-feedback actuators are disabled.

FFGFFS_POWERON

Indicates that power to the force-feedback system is currently available. If the device cannot report the power state, then neither FFGFFS_POWERON nor FFGFFS_POWEROFF should be returned.

FFGFFS_POWEROFF Indicates that power to the force-feedback system is not currently available. If the device cannot report the power state, then neither FFGFFS_POWERON nor FFGFFS_POWEROFF should be returned.

FFGFFS_SAFETYSWITCHON

Indicates that the safety switch (dead-man switch) is currently on, meaning that the device can operate. If the device cannot report the state of the safety switch, then neither FFGFFS_SAFETYSWITCHON nor FFGFFS_SAFETYSWITCHOFF should be returned.

FFGFFS_SAFETYSWITCHOFF

Indicates that the safety switch (dead-man switch) is currently off, meaning that the device cannot operate. If the device cannot report the state of the safety switch, then neither FFGFFS_SAFETYSWITCHON nor FFGFFS_SAFETYSWITCHOFF should be returned.

FFGFFS_USERFFSWITCHON

Indicates that the user force-feedback switch is currently on, meaning that the device can operate. If the device cannot report the state of the user force-feedback switch, then neither FFGFFS_USERFFSWITCHON nor FFGFFS_USERFFSWITCHOFF should be returned.

FFGFFS_USERFFSWITCHOFF

Indicates that the user force-feedback switch is currently off, meaning that the device cannot operate. If the device cannot report the state of the user force-feedback switch, then neither FFGFFS_USERFFSWITCHON nor FFGFFS_USERFFSWITCHOFF should be returned.

FFGFFS_DEVICELOST

Indicates that the device suffered an unexpected failure and is in an indeterminate state. It must be reset either by unacquiring and reacquiring the device, or by explicitly sending a FFSFFC_RESET command. For example, the device may be lost if the user suspends the computer, causing on-board memory on the device to be lost.

## See Also

### Instance Properties

dwLoad

A value indicating the percentage of device memory in use. A value of zero indicates that the device memory is completely available. A value of 100 indicates that the device is full

dwSize

Specifies the size of the structure in bytes. This member must be initialized before the structure is used.

