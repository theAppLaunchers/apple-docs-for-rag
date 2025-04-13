

- Foundation
- NSAppleEventDescriptor
-  list() 

Type Method

# list()

Creates and initializes an empty list descriptor.

Mac Catalyst 13.0+macOS 10.0+

``` source
class func list() -> NSAppleEventDescriptor
```

## Return Value

An empty list descriptor, or `nil` if an error occurs.

## Discussion

A list descriptor is a descriptor whose data consists of one or more descriptors. You can add items to the list by calling insert(_:at:) or remove them with remove(at:).

Invoking this method is equivalent to allocating an instance of `NSAppleEventDescriptor` and invoking init(listDescriptor:).

## See Also

### Creating and Initializing Descriptors

class func appleEvent(withEventClass: AEEventClass, eventID: AEEventID, targetDescriptor: NSAppleEventDescriptor?, returnID: AEReturnID, transactionID: AETransactionID) -> NSAppleEventDescriptor

Creates a descriptor that represents an Apple event, initialized according to the specified information.

init(boolean: Bool)

Creates a descriptor initialized with type `typeBoolean` that stores the specified Boolean value.

init(enumCode: OSType)

Creates a descriptor initialized with type `typeEnumerated` that stores the specified enumerator data type value.

init(int32: Int32)

Creates a descriptor initialized with Apple event type `typeSInt32` that stores the specified integer value.

init(string: String)

Creates a descriptor initialized with type `typeUnicodeText` that stores the text from the specified string.

init(typeCode: OSType)

Creates a descriptor initialized with type `typeType` that stores the specified type value.

class func null() -> NSAppleEventDescriptor

Creates and initializes a descriptor with no parameter or attribute values set.

class func record() -> NSAppleEventDescriptor

Creates and initializes a descriptor for an Apple event record whose data has yet to be set.

convenience init(listDescriptor: ())

Initializes a newly allocated instance as an empty list descriptor.

convenience init(recordDescriptor: ())

Initializes a newly allocated instance as a descriptor that is an Apple event record.

init(aeDescNoCopy: UnsafePointer&lt;AEDesc>)

Initializes a newly allocated instance as a descriptor for the specified Carbon `AEDesc` structure.

convenience init?(descriptorType: DescType, bytes: UnsafeRawPointer?, length: Int)

Initializes a newly allocated instance as a descriptor with the specified descriptor type and data (from an arbitrary sequence of bytes and a length count).

convenience init?(descriptorType: DescType, data: Data?)

Initializes a newly allocated instance as a descriptor with the specified descriptor type and data (from an instance of `NSData`).

convenience init(eventClass: AEEventClass, eventID: AEEventID, targetDescriptor: NSAppleEventDescriptor?, returnID: AEReturnID, transactionID: AETransactionID)

Initializes a newly allocated instance as a descriptor for an Apple event, initialized with the specified values.

