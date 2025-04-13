

- Kernel
- Deprecated Symbols
-  mbuf_tag_id_find Deprecated

Function

# mbuf_tag_id_find

macOS 10.4–10.15.4Deprecated

``` source
errno_t mbuf_tag_id_find(const char *module_string, mbuf_tag_id_t *module_id);
```

## Parameters 

`module_string`  

A unique string identifying your module. Example: com.apple.nke.SharedIP.

`module_id`  

Upon return, a unique identifier for use with mbuf_tag\_\* functions. This identifier is valid until the machine is rebooted.

## Return Value

0 upon success otherwise the errno error.

## Discussion

Lookup the module id for a string. If there is no module id assigned to this string, a new module id will be assigned. The string should be the bundle id of the kext. In the case of a tag that will be shared across multiple kexts, a common bundle id style string should be used.

The lookup operation is not optimized. A module should call this function once during startup and chache the module id. The module id will not be resassigned until the machine reboots.

