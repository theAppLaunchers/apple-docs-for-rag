

- Device Management
- VPN
-  VPN.DNS 

Device Management Profile

# VPN.DNS

The dictionary to configure DNS settings for the VPN.

iOS 4.0+iPadOS 4.0+macOS 10.7+tvOS 17.0+visionOS 1.0+Device Assignment ServicesVPP License Management

``` source
object VPN.DNS
```

## Properties

`DNSProtocol`

`string`

 (Required) 

The transport protocol to communicate with the DNS server.

Possible Values: `Cleartext, HTTPS, TLS`

`DomainName`

`string`

The primary domain of the tunnel.

`PayloadCertificateUUID`

`string`

That UUID that points to an identity certificate payload. The system uses this identity to authenticate the user to the DNS resolver.

`SearchDomains`

`[string]`

The list of domain strings used to fully qualify single-label host names.

`ServerAddresses`

`[string]`

 (Required) 

The array of DNS server IP address strings. These IP addresses can be a mixture of IPv4 and IPv6 addresses.

`ServerName`

`string`

The hostname of a DNS-over-TLS server to validate the server certificate, as defined in RFC 7858. If `ServerAddresses` isn’t specified, the system uses the hostname to determine the server addresses. This key is required if the `DNSProtocol` is `TLS`.

`ServerURL`

`string`

The URI template of a DNS-over-HTTPS server, as defined in RFC 8484, which needs to use the `https://` scheme. The system uses the hostname or address in the URL to validate the server certificate. If `ServerAddresses` isn’t specified, the system uses the hostname or address in the URL to determine the server addresses. This key is required if the `DNSProtocol` is `HTTPS`.

`SupplementalMatchDomains`

`[string]`

The list of domain strings used to determine which DNS queries use the DNS resolver settings in `ServerAddresses`. The system uses this key to create a split DNS configuration where it resolves only hosts in certain domains using the tunnel’s DNS resolver. The system uses the default resolver for hosts that aren’t in one of the domains in this list.

If `SupplementalMatchDomains` contains the empty string it becomes the default domain.

Split-tunnel configurations can direct all DNS queries to the VPN DNS servers before the primary DNS servers. If the VPN tunnel becomes the network’s default route, the servers listed in `ServerAddresses` become the default resolver and the system ignores the `SupplementalMatchDomains` list.

`SupplementalMatchDomainsNoSearch`

`integer`

If `0`, append the domains in the `SupplementalMatchDomains` list to the resolver’s list of search domains.

Default: `0`

Possible Values: `0, 1`

## See Also

### Profiles

object VPN.AlwaysOn

The dictionary that contains IPSec settings.

object VPN.IKEv2

The dictionary to use for an IKEv2 VPN type.

object VPN.IPSec

The dictionary to use for an IPSec VPN type.

object VPN.IPv4

The dictionary that contains IPV4 settings.

object VPN.PPP

The dictionary that contains PPP settings.

object VPN.Proxies

The dictionary that contains the Proxies settings.

object VPN.VPN

The dictionary that contains VPN, IPSec, and IKEv2 settings.

object VPN.TransparentProxy

The dictionary to use for a transparent proxy VPN type.

object VPN.VendorConfig

The vendor-specific configuration dictionary.

