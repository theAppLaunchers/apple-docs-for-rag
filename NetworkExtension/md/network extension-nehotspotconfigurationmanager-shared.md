

- Network Extension
- NEHotspotConfigurationManager
-  shared 

Type Property

# shared

Instantiates NEHotspotConfigurationManager as a singleton, so it can be shared.

iOS 11.0+iPadOS 11.0+Mac Catalyst 13.1+visionOS 1.0+watchOS 7.0+

``` source
class var shared: NEHotspotConfigurationManager { get }
```

## See Also

### Creating configurations

func apply(NEHotspotConfiguration, completionHandler: (((any Error)?) -> Void)?)

Adds or updates a Wi-Fi network configuration after prompting the user for permission, and then attempts to join the network under certain conditions.

