

- Core Bluetooth
- CBPeripheral
-  discoverIncludedServices(\_:for:) 

Instance Method

# discoverIncludedServices(\_:for:)

Discovers the specified included services of a previously-discovered service.

iOS 5.0+iPadOS 5.0+Mac Catalyst 13.1+macOS 10.7+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func discoverIncludedServices(
    _ includedServiceUUIDs: [CBUUID]?,
    for service: CBService
)
```

## Parameters 

`includedServiceUUIDs`  

An array of CBUUID objects that you are interested in. Here, each CBUUID object represents a UUID that identifies the type of included service you want to discover.

`service`  

The previously-discovered service whose included services you want to discover.

## Discussion

You can provide an array of CBUUID objects—representing included service UUIDs—in the `includedServiceUUIDs` parameter. When you do, the peripheral returns only the services of the peripheral that match the provided UUIDs.

Note

If the `servicesUUIDs` parameter is `nil`, this method returns all of the peripheral’s available services. This is much slower than providing an array of service UUIDs to search for.

When the peripheral discovers one or more included services of the specified service, it calls the peripheral(_:didDiscoverIncludedServicesFor:error:) method of its delegate object. After the service discovers its included services, you can access them through the service’s includedServices property.

## See Also

### Discovering Services

func discoverServices([CBUUID]?)

Discovers the specified services of the peripheral.

var services: [CBService]?

A list of a peripheral’s discovered services.

