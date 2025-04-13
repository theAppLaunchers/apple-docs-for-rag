

- Core Media
-  CMMetadataDataTypeRegistryDataTypeIsBaseDataType(\_:) 

Function

# CMMetadataDataTypeRegistryDataTypeIsBaseDataType(\_:)

Returns a Boolean value that indicates whether a data type identifier represents a base data type.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.1+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 6.0+

``` source
func CMMetadataDataTypeRegistryDataTypeIsBaseDataType(_ dataType: CFString) -> Bool
```

## Parameters 

`dataType`  

Identifier of the data type to be queried.

## Return Value

kCFBooleanTrue if first data type conforms to the second data type; kCFBooleanFalse otherwise.

## Discussion

This is simply a convenience method to test to see if a given data type identifier is in the array returned by CMMetadataDataTypeRegistryGetBaseDataTypes().

## See Also

### Inspecting Metadata

func CMMetadataDataTypeRegistryDataTypeIsRegistered(CFString) -> Bool

Returns a Boolean value that indicates the registration status of a data type identifier.

func CMMetadataDataTypeRegistryGetDataTypeDescription(CFString) -> CFString

Returns the data type description if it exists.

func CMMetadataDataTypeRegistryGetConformingDataTypes(CFString) -> CFArray

Returns the conforming data types for the data type, if any.

func CMMetadataDataTypeRegistryDataTypeConformsToDataType(CFString, conformsTo: CFString) -> Bool

Returns a Boolean value that indicates whether a data type conforms to another data type.

func CMMetadataDataTypeRegistryGetBaseDataTypeForConformingDataType(CFString) -> CFString

Returns the base data type identifier that a data type conforms to.

func CMMetadataDataTypeRegistryGetBaseDataTypes() -> CFArray?

Returns an array of base data type identifiers.

