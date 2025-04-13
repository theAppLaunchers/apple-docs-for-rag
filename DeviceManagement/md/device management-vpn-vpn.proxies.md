

- Device Management
- VPN
-  VPN.Proxies 

Device Management Profile

# VPN.Proxies

The dictionary that contains the Proxies settings.

iOS 4.0+iPadOS 4.0+macOS 10.7+tvOS 17.0+visionOS 1.0+Device Assignment ServicesVPP License Management

``` source
object VPN.Proxies
```

## Properties

`HTTPEnable`

`integer`

If `1`, enables proxy for HTTP traffic.

Default: `0`

Possible Values: `0, 1`

`HTTPPort`

`integer`

The port number of the HTTP proxy. This field is required if `HTTPProxy` is specified.

Minimum: `0`

Maximum: `65535`

`HTTPProxy`

`string`

The host name of the HTTP proxy.

`HTTPProxyPassword`

`string`

The password used for authentication.

`HTTPProxyUsername`

`string`

The user name used for authentication.

`HTTPSEnable`

`integer`

If `true`, enables proxy for HTTPS traffic.

Default: `0`

Possible Values: `0, 1`

`HTTPSPort`

`integer`

The port number of the HTTPS proxy. This field is required if `HTTPSProxy` is specified.

Minimum: `0`

Maximum: `65535`

`HTTPSProxy`

`string`

The host name of the HTTPS proxy.

`ProxyAutoConfigEnable`

`integer`

If `true`, enables automatic proxy configuration.

Possible Values: `0, 1`

`ProxyAutoConfigURLString`

`string`

The URL to the location of the proxy auto-configuration file. Used only when `ProxyAutoConfigEnable` is `true`.

`ProxyAutoDiscoveryEnable`

`integer`

If `true`, enables proxy auto discovery.

Default: `1`

Possible Values: `0, 1`

`SupplementalMatchDomains`

`[string]`

An array of domains that defines which hosts use proxy settings for hosts.

## Discussion

The system uses this dictionary when the `VPNType` is `Proxies`.

## See Also

### Profiles

object VPN.AlwaysOn

The dictionary that contains IPSec settings.

object VPN.DNS

The dictionary to configure DNS settings for the VPN.

object VPN.IKEv2

The dictionary to use for an IKEv2 VPN type.

object VPN.IPSec

The dictionary to use for an IPSec VPN type.

object VPN.IPv4

The dictionary that contains IPV4 settings.

object VPN.PPP

The dictionary that contains PPP settings.

object VPN.VPN

The dictionary that contains VPN, IPSec, and IKEv2 settings.

object VPN.TransparentProxy

The dictionary to use for a transparent proxy VPN type.

object VPN.VendorConfig

The vendor-specific configuration dictionary.

