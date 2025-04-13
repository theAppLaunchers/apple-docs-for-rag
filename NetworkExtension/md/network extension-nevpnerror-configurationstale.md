

- Network Extension
- NEVPNError
-  configurationStale 

Type Property

# configurationStale

An error code that indicates another process modfied the VPN configuration since the last time the app loaded the configuration.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.1+macOS 10.11+tvOS 17.0+visionOS 1.0+

``` source
static var configurationStale: NEVPNError.Code { get }
```

## Discussion

This error also occurs if the app tries to save the VPN configuration before loading it from the Network Extension preferences the first time after the app launches.

## See Also

### Error codes

static var configurationDisabled: NEVPNError.Code

An error code that indicates the VPN configuration associated with the VPN manager isn’t enabled.

static var configurationInvalid: NEVPNError.Code

An error code that indicates the VPN configuration associated with the VPN manager object is invalid.

static var connectionFailed: NEVPNError.Code

An error code that indicates the connection to the VPN server failed.

static var configurationReadWriteFailed: NEVPNError.Code

An error code that indicates an error occurred while reading or writing the Network Extension preferences.

static var configurationUnknown: NEVPNError.Code

An error code that indicates that unspecified error occurred.

