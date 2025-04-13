

- Core Foundation
-  CFDictionaryAddValue(\_:\_:\_:) 

Function

# CFDictionaryAddValue(\_:\_:\_:)

Adds a key-value pair to a dictionary if the specified key is not already present.

iOSiPadOSMac CatalystmacOStvOSvisionOSwatchOS

``` source
func CFDictionaryAddValue(
    _ theDict: CFMutableDictionary!,
    _ key: UnsafeRawPointer!,
    _ value: UnsafeRawPointer!
)
```

## Parameters 

`theDict`  

The dictionary to modify. If the dictionary is a fixed-capacity dictionary and it is full before this operation, the behavior is undefined.

`key`  

The key for the value to add to the dictionary—a CFType object or a pointer value. The `key` is retained by the dictionary using the retain callback provided when the dictionary was created, so must be of the type expected by the callback. If a key which matches `key` is already present in the dictionary, this function does nothing (“add if absent”).

`value`  

A CFType object or a pointer value to add to the dictionary. The `value` is retained by the dictionary using the retain callback provided when the dictionary was created, so must be of the type expected by the callback.

## See Also

### Modifying a Dictionary

func CFDictionaryRemoveAllValues(CFMutableDictionary!)

Removes all the key-value pairs from a dictionary, making it empty.

func CFDictionaryRemoveValue(CFMutableDictionary!, UnsafeRawPointer!)

Removes a key-value pair.

func CFDictionaryReplaceValue(CFMutableDictionary!, UnsafeRawPointer!, UnsafeRawPointer!)

Replaces a value corresponding to a given key.

func CFDictionarySetValue(CFMutableDictionary!, UnsafeRawPointer!, UnsafeRawPointer!)

Sets the value corresponding to a given key.

