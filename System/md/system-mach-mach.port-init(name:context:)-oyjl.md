

- System
- Mach
- Mach.Port
-  init(name:context:) 

Initializer

# init(name:context:)

Transfer ownership of an existing, unmanaged, but already guarded, Mach port right into a Mach.Port by name.

iOS 17.4+iPadOS 17.4+Mac Catalyst 17.4+macOS 14.4+tvOS 17.4+visionOS 1.0+watchOS 10.4+

``` source
init(
    name: mach_port_name_t,
    context: mach_port_context_t
)
```

Available when `RightType` is `Mach.ReceiveRight`.

## Discussion

This initializer aborts if name is MACH_PORT_NULL.

If the type of the right does not match the type T of Mach.Port being constructed, the behavior is undefined.

The underlying port right will be automatically deallocated when the Mach.Port object is destroyed.

