

- Network Extension
- NEDNSSettings
-  dnsProtocol 

Instance Property

# dnsProtocol

The DNS protocol used by the server, such as HTTPS or TLS.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+macOS 11.0+tvOS 17.0+visionOS 1.0+

``` source
var dnsProtocol: NEDNSProtocol { get }
```

## Discussion

By default, an NEDNSSettings object will use NEDNSProtocol.cleartext. In order to use encryption, create an NEDNSOverHTTPSSettings or NEDNSOverTLSSettings object.

## See Also

### Accessing DNS properties

var servers: [String]

The DNS server IP addresses.

var searchDomains: [String]?

A list of domain strings used to fully qualify single-label host names.

var domainName: String?

The primary domain of the tunnel.

var matchDomains: [String]?

A list of domain strings used to determine which DNS queries will use the DNS resolver settings contained in this object.

var matchDomainsNoSearch: Bool

A Boolean that specifies if the domains in the `matchDomains` list should not be appended to the resolver’s list of search domains.

enum NEDNSProtocol

