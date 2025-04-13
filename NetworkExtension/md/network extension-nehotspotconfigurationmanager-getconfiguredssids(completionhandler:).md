

- Network Extension
- NEHotspotConfigurationManager
-  getConfiguredSSIDs(completionHandler:) 

Instance Method

# getConfiguredSSIDs(completionHandler:)

Submits a completion handler the configuration manager calls to send your app the names of the SSIDs or Wi-Fi hotspot domains in the configuration.

iOS 11.0+iPadOS 11.0+Mac Catalyst 13.1+visionOS 1.0+watchOS 7.0+

``` source
func getConfiguredSSIDs(completionHandler: @escaping ([String]) -> Void)
```

``` source
func configuredSSIDs() async -> [String]
```

## Parameters 

`completionHandler`  

A completion handler that accepts an array of strings.

## Discussion

The hotspot configuration manager sends your app a list of network SSIDs or Hotspot 2.0 domain names from the configuration by calling the completion handler you pass to the method.

For Hotspot 2.0 Enterprise (802.1X) networks, the list contains HS 2.0 domain names, and for other Wi-Fi networks, it contains their SSID.

