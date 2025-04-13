

- Network Extension
- NEHotspotHS20Settings
-  mccAndMNCs 

Instance Property

# mccAndMNCs

An array of Mobile Country Code (MCC) and Mobile Network Code (MNC) pairs used for Wi-Fi Hotspot 2.0 negotiation.

iOS 11.0+iPadOS 11.0+Mac Catalyst 13.1+visionOS 1.0+

``` source
var mccAndMNCs: [String] { get set }
```

## Discussion

Each `MCCAndMNCs` string must contain exactly six integers.

## See Also

### Accessing Hotspot 2.0 properties

var domainName: String

The domain name of a Hotspot 2.0 Wi-Fi Network.

var isRoamingEnabled: Bool

A Boolean value indicating whether or not roaming is enabled on a Hotspot 2.0 Wi-Fi network.

var naiRealmNames: [String]

An array of Network Access Identifier (NAI) realm name strings used for Wi-Fi Hotspot 2.0 negotiation.

var roamingConsortiumOIs: [String]

An array of Roaming Consortium Organization (RCO) identifiers used for Wi-Fi Hotspot 2.0 negotiation.

