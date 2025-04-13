

- External Accessory
- EAAccessoryManager
-  showBluetoothAccessoryPicker(withNameFilter:completion:) 

Instance Method

# showBluetoothAccessoryPicker(withNameFilter:completion:)

Displays an alert that allows the user to pair the device with a Bluetooth accessory.

iOS 6.0+iPadOS 6.0+Mac Catalyst 14.0+tvOS 10.0+visionOS 1.0+

``` source
func showBluetoothAccessoryPicker(
    withNameFilter predicate: NSPredicate?,
    completion: EABluetoothAccessoryPickerCompletion? = nil
)
```

``` source
func showBluetoothAccessoryPicker(withNameFilter predicate: NSPredicate?) async throws
```

## Parameters 

`predicate`  

The predicate is evaluated using the name of the Bluetooth accessory. The picker displays only devices with names that match the predicate. If you specify `nil`, this method displays all discovered accessories.

`completion`  

A completion block to execute when the picker is dismissed. Use this block to track any errors that might occur during the pairing process.

## Discussion

Important

You can call this method from synchronous code using a completion handler, as shown on this page, or you can call it as an asynchronous method that has the following declaration:

```
```

For information about concurrency and asynchronous code in Swift, see Calling Objective-C APIs Asynchronously.

On iOS devices, this method synchronously displays an alert containing the list of Bluetooth accessories that have been discovered by the current device and that match the specified filter (if any). The user can select an accessory from this list and pair the device to it. Pairing an accessory updates the accessory manager’s list of connected accessories and generates a corresponding connection notification. On Apple silicon, this method displays an alert to let the user know that the Bluetooth accessory picker is unavailable.

Note

The picker displays only Bluetooth devices that include an iAP over Bluetooth unique ID in their extended inquiry response.

## See Also

### Presenting the Bluetooth Picker

typealias EABluetoothAccessoryPickerCompletion

The completion block for the Bluetooth picker.

struct EABluetoothAccessoryPickerError

Error codes returned by the Bluetooth accessory picker.

enum Code

The error codes that may be passed in an error object for the Bluetooth picker completion block.

let EABluetoothAccessoryPickerErrorDomain: String

The domain for errors passed to a Bluetooth picker completion block.

