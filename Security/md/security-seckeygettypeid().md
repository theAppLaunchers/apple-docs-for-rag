

- Security
-  SecKeyGetTypeID() 

Function

# SecKeyGetTypeID()

Returns the unique identifier of the opaque type to which a key object belongs.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.1+macOS 10.3+tvOS 4.0+visionOS 1.0+watchOS 1.0+

``` source
func SecKeyGetTypeID() -> CFTypeID
```

## Return Value

A value that identifies the opaque type of a SecKey object.

## Discussion

This function returns a value that uniquely identifies the opaque type of a SecKey object. You can compare this value to the CFTypeID identifier obtained by calling the CFGetTypeID(_:) function on a specific object. These values might change from release to release or platform to platform.

