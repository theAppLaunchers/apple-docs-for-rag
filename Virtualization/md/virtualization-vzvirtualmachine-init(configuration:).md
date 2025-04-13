

- Virtualization
- VZVirtualMachine
-  init(configuration:) 

Initializer

# init(configuration:)

Creates the VM and configures it with the specified data.

macOS 11.0+

``` source
convenience init(configuration: VZVirtualMachineConfiguration)
```

## Parameters 

`configuration`  

The configuration of the VM. The configuration must be valid, and you can verify that it’s valid by calling its validate() method. The VM stores a copy of the configuration.

## Return Value

An initialized VM object.

## Discussion

This VM uses your app’s main queue for all operations. You must perform all VM-related operations on the main queue, and the VM executes all callbacks and delegate methods on the main queue.

## See Also

### Creating the VM

init(configuration: VZVirtualMachineConfiguration, queue: dispatch_queue_t)

Creates and configures the VM with the specified data and dispatch queue.

class var isSupported: Bool

A Boolean value that indicates whether the system supports virtualization.

