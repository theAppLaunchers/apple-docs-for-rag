

- IOBluetooth
- IOBluetoothDevice
-  rssi() 

Instance Method

# rssi()

Get the RSSI device (if connected), above or below the golden range. If the RSSI is within the golden range, a value of 0 is returned. For the actual RSSI value, use getRawRSSI. For more information, see the Bluetooth 4.0 Core Specification.

macOS 10.7+

``` source
func rssi() -> BluetoothHCIRSSIValue
```

## Return Value

Returns the RSSI of the device. If the value cannot be read (e.g. the device is disconnected), a value of +127 will be returned.

