

- QuickTime File Format
-  Country list atom ('ctry') 

Atom

# Country list atom ('ctry')

An atom that lists items that are suitable for more than one country.

## Overview

When one or more items must be identified as being suitable for more than one country, each list of countries is stored in this otherwise optional atom. The country list atom is a full atom with an atom type of `‘ctry’`.

Each list starts with a two-byte count of the number of items in the list, and then each ISO 3166 code representing countries in the list.

The atom consists of a count of the number of lists, expressed as a 32-bit integer, and then these lists, appended end-to-end.

Note that:

- Indexes into the country list atom are 1-based.

- Zero (0) is reserved and never used as an index.

- Currently, there is a limit of 255 countries that may be recorded in a country list atom.

An example country list atom consisting of two country lists with two and three countries, respectively, is shown in the following table.

| Field size | Field | Field contents | Comment |
|----|----|----|----|
| 32-bit | atom_size | 26 | Size of this country list atom in bytes. |
| 32-bit | atom_type | `'ctry'` |  |
| 32-bit | entry_count | 2 | Number of country lists. |
| 16-bit | country_count | 2 | Number of countries in country list 1. |
| 16-bit | country | ‘US’ |  |
| 16-bit | country | ‘UK’ |  |
| 16-bit | country_count | 3 | Number of countries in country list 2. |
| 16-bit | country | ‘JP’ |  |
| 16-bit | country | ‘US’ |  |
| 16-bit | country | ‘FR’ |  |

## Topics

### Data fields

Size

A 32-bit unsigned integer that indicates the size in bytes of the atom structure.

Type

A 32-bit unsigned integer value.

Version

One byte.

Flags

Three bytes.

Entry_count

A 32-bit integer indicating the number of Country arrays to follow in this atom.

Country_count

A 16-bit integer indicating the number of Countries in the array.

Country_Country_count

An array of 16-bit integers, defined according to the ISO 3166 definition of country codes.

## See Also

### Atoms

Language list atom ('lang')

An atom that lists items that are suitable for more than one language.

Metadata item keys atom ('keys')

An atom that holds a list of the metadata keys that may be present in the metadata atom.

Metadata item list atom ('ilst')

An atom that holds a list of actual metadata values that are present in the metadata atom.

Metadata item atom

An atom that holds a metadata value.

Value atom

An atom that expresses a metadata value.

Item information atom ('itif')

An atom that contains information about the item, including item-specific flags and item optional identifier.

Name atom ('name')

An atom you use to provide a name for a metadata item.

Data atom ('data')

An atom that contains the type and locale specific value of metadata.

