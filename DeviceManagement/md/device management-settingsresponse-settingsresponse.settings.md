

- Device Management
- SettingsResponse
-  SettingsResponse.Settings 

Device Management Command

# SettingsResponse.Settings

A dictionary that describes the results of configuring settings on a device.

iOS 5.0+iPadOS 5.0+macOS 10.9+tvOS 9.0+visionOS 1.1+watchOS 10.0+Device Assignment ServicesVPP License Management

``` source
object SettingsResponse.Settings
```

## Properties

`ErrorChain`

`[`SettingsResponse.Settings.ErrorChainItem`]`

An array of dictionaries that describes any errors that occurred.

`Identifier`

`string`

The app identifier to which this error applies.

Note

For a watchOS app, the identifier is the watch’s bundle identifier, which differs from the main bundle identifier for the iPhone to which the watch is paired.

`Status`

`string`

 (Required) 

The status of the setting, which is one of the following values:

- `Acknowledged`: The device processed the command successfully.

- `Error`: An error occurred. See the `ErrorChain` for more details.

## Topics

### Commands

object SettingsResponse.Settings.ErrorChainItem

A dictionary that describes an error chain item.

## See Also

### Commands

object SettingsResponse.ErrorChainItem

A dictionary that describes an error chain item.

