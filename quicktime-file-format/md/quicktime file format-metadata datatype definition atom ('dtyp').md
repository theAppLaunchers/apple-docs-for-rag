

- QuickTime File Format
-  Metadata datatype definition atom ('dtyp') 

Atom

# Metadata datatype definition atom ('dtyp')

An atom you use to specify the data type of the metadata key atom’s value.

## Overview

A metadata datatype definition atom can be used to specify the data type of the metadata key atom’s value. The type of the metadata datatype definition atom is `‘dtyp’`.

The layout of a metadata datatype definition atom is as follows:

| Data field | Bytes |
|----|----|
| Size | 4 |
| Type = `'dtyp'` | 4 |
| Datatype namespace | 4 |
| Datatype array | variable |

The combination of `datatype namespace` and `datatype array` indicate the data type (or structure) of a metadata item value. The `datatype namespace` type indicates the interpretation of the `datatype array` value. This specification defines two `datatype namespace` types:

- If `datatype namespace` is `0`, `datatype array` contains a big-endian 32-bit unsigned integer corresponding to a well-known type specified in Well-known types. For example, a well-known type of `1` indicates UTF-8 text and `23` indicates a big-endian 32-bit floating-point number.

- If `datatype namespace` is `1`, `datatype array` contains a reverse-address style UTF-8 string indicating an extended data type. This data type namespace type can be used if the data type does not have a corresponding well-known data type. `Datatype array` consists of the bytes of a case-sensitive UTF-8 string without a null (`‘\0’`) terminator. For example, a hypothetical `datatype array` “com.company.my-custom-datatype” could register a custom data type belonging to the owner of the DNS registration “mycompany.com”.

A `datatype namespace` other than `0` or `1` may occur in a timed metadata track, perhaps written according to a later version of this specification. Metadata item values with unrecognized data types should be ignored. Even so, some processing is still possible on the metadata item with unrecognized data type, such as copying it between tracks.

Note

New datatype namespaces must be registered with Apple.

Note

Many uses for proprietary or custom metadata data types can be satisfied by using the extended data type namespace type code `1`. This allows the new data type to be specified without registration. The reason to add a custom `datatype namespace` type is to allow an existing numbering or naming scheme from a foreign metadata standard to be used with metadata items.

## Topics

### Data fields

Size

A 32-bit unsigned integer that indicates the size in bytes of the atom structure.

Type

A 32-bit unsigned integer value.

Datatype namespace

A 32-bit identifier describing how to interpret the data type for the value.

Datatype array

An array of unsigned 8-bit bytes holding the data type designation for values in timed metadata media samples having this key.

## See Also

### Describing timed metadata

Metadata key table atom ('keys')

An atom that contains a table of keys and mappings to payload data in the corresponding timed metadata media samples.

Bit rate atom ('btrt')

An atom that signals the bit rate information of a stream.

Metadata key atom

An atom that contains a key that corresponds to the timed metadata track containing it.

Metadata key declaration atom ('keyd')

An atom that holds the key namespace and key value of that namespace for the given values.

Metadata locale atom ('loca')

An atom that tags a metadata value with a locale.

