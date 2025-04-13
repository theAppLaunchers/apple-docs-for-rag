

- Network Extension
- NETunnelProviderManager
-  safariDomains 

Instance Property

# safariDomains

The website domains that the system routes connections from the Safari app through a per-app VPN.

macOS 10.15.4+

``` source
var safariDomains: [String] { get set }
```

## Discussion

For per-app VPNs only, when the user navigates in Safari to a website within one of these domains, the system routes the website traffic through the VPN.

## See Also

### Configuring a per-app VPN

class func forPerAppVPN() -> Self

Returns a tunnel provider manager for managing a per-app VPN configuration.

var appRules: [NEAppRule]

The rules for specific apps in a per-app VPN.

var excludedDomains: [String]

The domains that the system excludes from a per-app VPN.

var associatedDomains: [String]

The domains that the system routes network traffic through for a per-app VPN.

var calendarDomains: [String]

The calendar servers that the system routes connections from the Calendar app through for a per-app VPN.

var contactsDomains: [String]

The contacts servers that the system routes connections from the Contacts app through for a per-app VPN.

var mailDomains: [String]

The mail servers that the system routes connections from the Mail app through for a per-app VPN.

