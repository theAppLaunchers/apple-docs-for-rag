

- Network Extension
- NEHotspotEAPSettings
-  isTLSClientCertificateRequired 

Instance Property

# isTLSClientCertificateRequired

A Boolean value indicating whether a network requires two-factor authentication or allows zero-factor authentication.

iOS 11.0+iPadOS 11.0+Mac Catalyst 13.1+visionOS 1.0+

``` source
var isTLSClientCertificateRequired: Bool { get set }
```

## Return Value

If `true`, the Wi-Fi network requires two-factor authentication for EAP-TTLS, PEAP and EAP-FAST. If `false`, the network requires zero-factor authentication for EAP-TLS. The default values are `true` if the EAP type is EAP-TLS and `false` for other EAP types.

## Discussion

Optional. EAP Transport Layer Security (EAP-TLS) is an IETF open security standard that requires a client certificate in addition to a password (two-factor authentication). If an EAP-TTLS, PEAP or EAP-FAST network requires two-factor authentication then a client identity must be configured. If `isTLSClientCertificateRequired` returns false, a client identity need not be configured. If `isTLSClientCertificateRequired` returns true, your app must set the client identity by using setIdentity(_:).

## See Also

### Accessing EAP properties

var trustedServerNames: [String]

An array of server certificate common name strings used to verify a server’s certificate.

var supportedEAPTypes: [NSNumber]

An array of supported EAP types.

enum EAPType

The EAP types that may be specified in supportedEAPTypes.

var username: String

The user name string for EAP authentication, encoded as UTF-8.

var password: String

The password component of the IEEE 802.1X authentication credential.

var preferredTLSVersion: NEHotspotEAPSettings.TLSVersion

The Transport Layer Security (TLS) version to use during a TLS authentication handshake.

enum TLSVersion

The EAPTLS Version identifiers that may be specified by preferredTLSVersion.

var outerIdentity: String

The identity string to be used in the EAP-Identity/Response packet during outer EAP authentication.

var ttlsInnerAuthenticationType: NEHotspotEAPSettings.TTLSInnerAuthenticationType

The inner-layer authentication protocol used by a TTLS module.

enum TTLSInnerAuthenticationType

The TTLS Inner Authentication Types that may be specified by NEHotspotEAPSettings.TTLSInnerAuthenticationType.

