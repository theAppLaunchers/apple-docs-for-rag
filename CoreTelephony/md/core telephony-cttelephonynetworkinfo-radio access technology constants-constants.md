

- Core Telephony
- CTTelephonyNetworkInfo
-  Radio Access Technology Constants 

API Collection

# Radio Access Technology Constants

Constants that describe the current radio access technology.

## Topics

### Constants

let CTRadioAccessTechnologyGPRS: String

The General Packet Radio Service (GPRS) radio access technology.

let CTRadioAccessTechnologyEdge: String

The Enhanced Data rates for GSM Evolution (EDGE) radio access technology.

let CTRadioAccessTechnologyWCDMA: String

The Wideband Code Division Multiple Access (WCDMA) radio access technology.

let CTRadioAccessTechnologyHSDPA: String

The High-Speed Downlink Packet Access (HSDPA) radio access technology.

let CTRadioAccessTechnologyHSUPA: String

The High-Speed Uplink Packet Acess (HSUPA) radio access technology.

let CTRadioAccessTechnologyCDMA1x: String

The Code Division Multiple Access (CDMA) 1x radio access technology.

let CTRadioAccessTechnologyCDMAEVDORev0: String

The Code Division Multiple Access (CDMA) Evolution-Data Optimized (EV-DO) Rev. 0 radio access technology.

let CTRadioAccessTechnologyCDMAEVDORevA: String

The Code Division Multiple Access (CDMA) Evolution-Data Optimized (EV-DO) Rev. A radio access technology.

let CTRadioAccessTechnologyCDMAEVDORevB: String

The Code Division Multiple Access (CDMA) Evolution-Data Optimized (EV-DO) Rev. B radio access technology.

let CTRadioAccessTechnologyeHRPD: String

The Enhanced High Rate Packet Data (eHRPD) radio access technology.

let CTRadioAccessTechnologyLTE: String

The Long-Term Evolution (LTE) radio access technology.

let CTRadioAccessTechnologyNRNSA: String

The 5G New Radio Non-Standalone (NRNSA) radio access technology.

let CTRadioAccessTechnologyNR: String

The 5G New Radio (NR) radio access technology.

## See Also

### Getting Information About the Cellular Service Provider

var dataServiceIdentifier: String?

The identifier of the service that’s currently providing data.

var delegate: (any CTTelephonyNetworkInfoDelegate)?

An object that the system notifies when the data service identifier changes.

protocol CTTelephonyNetworkInfoDelegate

The methods that the system invokes when data service changes occur.

var serviceCurrentRadioAccessTechnology: [String : String]?

A dictionary containing the current radio access technology registered to each service.

