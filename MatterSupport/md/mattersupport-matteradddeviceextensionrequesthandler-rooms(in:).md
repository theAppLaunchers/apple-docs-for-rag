

- MatterSupport
- MatterAddDeviceExtensionRequestHandler
-  rooms(in:) 

Instance Method

# rooms(in:)

Provides rooms that correspond to a home in the device setup.

iOS 16.1+iPadOS 16.1+Mac CatalystmacOS 14.0+visionOS

``` source
func rooms(in home: MatterAddDeviceRequest.Home?) async -> [MatterAddDeviceRequest.Room]
```

## Return Value

The list of rooms to show. If only one room exists, no room card appears.

## Discussion

The system issues this request before presenting the “Select Room” card, and populates the picker with these options.

If the returned array contains two or more rooms, the user-interface flow displays a picker to allow selection of a room. If the object contains one room, that room is the selected room and the user-interface flow doesn’t display a picker. If the object contains no room, then the user-interface flow doesn’t display a picker, and any methods that take a room parameter receive `nil`.

## See Also

### Configuring and validating the device

func configureDevice(named: String, in: MatterAddDeviceRequest.Room?) async

Configures the device with selected attributes.

func validateDeviceCredential(MatterAddDeviceExtensionRequestHandler.DeviceCredential) async throws

Performs verification and attestation checks.

struct DeviceCredential

A collection of device credentials the device presents during commissioning.

