

- Core Foundation
-  CFAllocatorGetContext(\_:\_:) 

Function

# CFAllocatorGetContext(\_:\_:)

Obtains the context of the specified allocator or of the default allocator.

iOSiPadOSMac CatalystmacOStvOSvisionOSwatchOS

``` source
func CFAllocatorGetContext(
    _ allocator: CFAllocator!,
    _ context: UnsafeMutablePointer!
)
```

## Parameters 

`allocator`  

The allocator to examine. Pass `NULL` to obtain the context of the default allocator.

`context`  

On return, contains the context of `allocator`.

## Discussion

An allocator’s context, a structure of type `CFAllocatorContext`, holds pointers to various function callbacks (particularly those that allocate, reallocate, and deallocate memory for an object). The context also contains a version number and the `info` field for program-defined data. To obtain the value of the `info` field you usually first have to get an allocator’s context.

