

- System Configuration
-  SCDynamicStoreKeyCreateNetworkInterface(\_:\_:) 

Function

# SCDynamicStoreKeyCreateNetworkInterface(\_:\_:)

Creates a dynamic store key that can be used to access the network interface configuration information in the dynamic store.

macOS 10.1+

``` source
func SCDynamicStoreKeyCreateNetworkInterface(
    _ allocator: CFAllocator?,
    _ domain: CFString
) -> CFString
```

## Parameters 

`allocator`  

The allocator that should be used to allocate memory for this key. This parameter may be `NULL` in which case the current default allocator is used. If this value is not a valid CFAllocator, the behavior is undefined.

`domain`  

The desired domain, such as the requested configuration or the current state.

## Return Value

A string containing the formatted key.

## See Also

### Group

func SCDynamicStoreKeyCreateNetworkGlobalEntity(CFAllocator?, CFString, CFString) -> CFString

Creates a dynamic store key that can be used to access a specific global (as opposed to a per-service or per-interface) network configuration entity.

func SCDynamicStoreKeyCreateNetworkInterfaceEntity(CFAllocator?, CFString, CFString, CFString?) -> CFString

Creates a dynamic store key that can be used to access the per-interface network configuration information in the dynamic store.

func SCDynamicStoreKeyCreateNetworkServiceEntity(CFAllocator?, CFString, CFString, CFString?) -> CFString

Creates a dynamic store key that can be used to access the per-service network configuration information.

func SCDynamicStoreKeyCreateComputerName(CFAllocator?) -> CFString

Creates a key that can be used to receive notifications when the current computer name changes.

func SCDynamicStoreKeyCreateConsoleUser(CFAllocator?) -> CFString

Creates a key that can be used to receive notifications when the current console user changes.

func SCDynamicStoreKeyCreateHostNames(CFAllocator?) -> CFString

Creates a key that can be used to receive notifications when the `HostNames` entity changes.

func SCDynamicStoreKeyCreateLocation(CFAllocator?) -> CFString

Creates a key that can be used to receive notifications when the location identifier changes.

func SCDynamicStoreKeyCreateProxies(CFAllocator?) -> CFString

Creates a key that can be used to receive notifications when the current network proxy settings are changed.

