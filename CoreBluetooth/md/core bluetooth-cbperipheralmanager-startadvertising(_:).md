

- Core Bluetooth
- CBPeripheralManager
-  startAdvertising(\_:) 

Instance Method

# startAdvertising(\_:)

Advertises peripheral manager data.

iOS 6.0+iPadOS 6.0+Mac Catalyst 13.1+macOS 10.9+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func startAdvertising(_ advertisementData: [String : Any]?)
```

## Parameters 

`advertisementData`  

An optional dictionary containing the data you want to advertise. The peripheral manager only supports two keys: CBAdvertisementDataLocalNameKey and CBAdvertisementDataServiceUUIDsKey.

## Discussion

When you start advertising peripheral data, the peripheral manager calls the peripheralManagerDidStartAdvertising(_:error:) method of its delegate object.

Core Bluetooth advertises data on a “best effort” basis, due to limited space and because there may be multiple apps advertising simultaneously. While in the foreground, your app can use up to 28 bytes of space in the initial advertisement data for any combination of the supported advertising data keys. If no this space remains, there’s an additional 10 bytes of space in the scan response, usable only for the local name (represented by the value of the CBAdvertisementDataLocalNameKey key). Note that these sizes don’t include the 2 bytes of header information required for each new data type.

Any service UUIDs contained in the value of the CBAdvertisementDataServiceUUIDsKey key that don’t fit in the allotted space go to a special “overflow” area. These services are discoverable only by an iOS device explicitly scanning for them.

While your app is in the background, the local name isn’t advertised and all service UUIDs are in the overflow area.

For details about the format of advertising and response data, see the Bluetooth 4.0 specification, Volume 3, Part C, Section 11.

## Topics

### Related Documentation

let CBAdvertisementDataOverflowServiceUUIDsKey: String

An array of UUIDs found in the overflow area of the advertisement data.

## See Also

### Managing Advertising

Advertising Data

func stopAdvertising()

Stops advertising peripheral manager data.

var isAdvertising: Bool

A Boolean value that indicates whether the peripheral is advertising data.

