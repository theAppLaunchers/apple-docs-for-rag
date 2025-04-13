

- Foundation
- NSAppleEventDescriptor
-  record() 

Type Method

# record()

Creates and initializes a descriptor for an Apple event record whose data has yet to be set.

Mac Catalyst 13.0+macOS 10.0+

``` source
class func record() -> NSAppleEventDescriptor
```

## Return Value

An Apple event descriptor whose data has yet to be set, or `nil` if an error occurs.

## Discussion

An Apple event record is a descriptor whose data is a set of descriptors keyed by four-character codes. You can add information to the descriptor with methods such as setAttribute(_:forKeyword:), setDescriptor(_:forKeyword:), and setParam(_:forKeyword:).

Invoking this method is equivalent to allocating an instance of `NSAppleEventDescriptor` and invoking init(recordDescriptor:).

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

class func list() -> NSAppleEventDescriptor

Creates and initializes an empty list descriptor.

class func null() -> NSAppleEventDescriptor

Creates and initializes a descriptor with no parameter or attribute values set.

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

