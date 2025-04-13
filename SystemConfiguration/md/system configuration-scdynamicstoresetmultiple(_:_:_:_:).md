

- System Configuration
-  SCDynamicStoreSetMultiple(\_:\_:\_:\_:) 

Function

# SCDynamicStoreSetMultiple(\_:\_:\_:\_:)

Updates multiple values in the dynamic store.

macOS 10.1+

``` source
func SCDynamicStoreSetMultiple(
    _ store: SCDynamicStore?,
    _ keysToSet: CFDictionary?,
    _ keysToRemove: CFArray?,
    _ keysToNotify: CFArray?
) -> Bool
```

## Parameters 

`store`  

The dynamic store session.

`keysToSet`  

A dictionary of key-value pairs to add to the dynamic store.

`keysToRemove`  

An array of keys to remove from the dynamic store.

`keysToNotify`  

An array of keys to flag as changed (without changing their values).

## Return Value

`TRUE` if the dynamic store updates were successful; otherwise, `FALSE`.

## See Also

### Adding or Updating Keys and Values

func SCDynamicStoreAddTemporaryValue(SCDynamicStore, CFString, CFPropertyList) -> Bool

Temporarily adds the specified key-value pair to the dynamic store, if no such key already exists.

func SCDynamicStoreAddValue(SCDynamicStore?, CFString, CFPropertyList) -> Bool

Adds the specified key-value pair to the dynamic store, if no such key already exists.

func SCDynamicStoreSetValue(SCDynamicStore?, CFString, CFPropertyList) -> Bool

Adds or replaces a value in the dynamic store for the specified key.

