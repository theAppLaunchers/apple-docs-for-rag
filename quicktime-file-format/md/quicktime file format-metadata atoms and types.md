

- QuickTime File Format
-  Metadata atoms and types 

API Collection

# Metadata atoms and types

Store metadata in QuickTime Movie files.

## Overview

Metadata can be defined as useful information related to media. This section describes a method of associating metadata with media in a QuickTime file that is extensible and allows for language and country tagging. In addition, it provides a means to store the type of the metadata and associate a name with metadata. This method of storing metadata is supported in both QuickTime 7 and QuickTime X.

This metadata format uses a key–value pair for each type of metadata being stored. Standard keys, with specific formats for the values they indicate, have been defined. See QuickTime metadata keys for details.

Note

The QuickTime file format also defines user data which, in some limited cases, can be used to store metadata. The method of storing metadata defined in this section provides an extensible and flexible design for handling a wide variety of metadata types.

### Data type

The storage type of metadata items is defined via an enumerated list of data types, defined statically; an example might be “plain Unicode text”. See the Well-known types table for details of the standard, defined data types.

### Meaning or purpose

The meaning of a metadata item identifies what it represents: a copyright notice, the performer’s name, and so on. It uses an extensible namespace allowing for meanings or keys to be added, and then referenced, from metadata items. These keys may be four-character codes, names in reverse-address format (such as “com.apple.quicktime.windowlocation”) or any other key format including native formats from external metadata standards. A key is tagged with its namespace allowing for extension in the future. It is recommended that reverse-address format be used in the general case: this provides an extensible syntax for vendor data or for other organizations or standards bodies.

### Data location

Metadata is stored immediately in the corresponding atom structures, by value.

### Localization

A metadata item can be identified as specific to a country or set of countries, to a language or set of languages, or to some combination of languages and countries. This identification allows for a default value (suitable for any language or country not explicitly called out), a single value, or a list of values.

### Storage Location in a QuickTime File

Within a QuickTime file, metadata can be stored within a movie atom (`‘moov’`), a track atom (`‘trak’`) or a media atom (`‘mdia’`). Only one metadata atom is allowed for each location. If there is user data and metadata stored in the same location, and both declare the same information, for example, declare a copyright notice, the metadata takes precedence.

### Metadata structure

The container for metadata is an atom of type `‘meta’`. The metadata atom must contain the following subatoms: metadata handler atom (`‘hdlr’`), metadata item keys atom (`‘keys’`), and metadata item list atom (`‘ilst’`). Other optional atoms that may be contained in a metadata atom include the country list atom (`‘ctry’`), language list atom (`‘lang’`) and free space atom (`‘free’`). The country list and language list atoms can be used to store localized data in an efficient manner. The free space atom may be used to reserve space in a metadata atom for later additions to it, or to zero out bytes within a metadata atom after editing and removing elements from it. The free space atom may not occur within any other subatom contained in the metadata atom.

## Topics

### Metadata structure

Metadata atom ('meta')

An atom that is the container for carrying metadata.

Metadata handler atom ('hdlr')

An atom that defines the structure used for all types of metadata stored within the metadata atom.

Metadata header atom ('mhdr')

An atom that holds the integer value for the next unique item identifier to assign.

### Atoms

Country list atom ('ctry')

An atom that lists items that are suitable for more than one country.

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

### Types and usage

Extensibility

Avoid issues building extensibility into your file.

Localization list sets

Provide metadata for more than one country or language.

Type indicator

Four bytes that indicate a type of data that QuickTime supports.

Locale indicator

A four-byte value that indicates a locale.

Data ordering

Represent multiple representations of the same information, differing either by language or storage type or by the size or nature of the data.

Well-known types

Basic data types.

Location metadata

Storing the location coordinates, as well as several auxiliary pieces of information about a location, as metadata.

QuickTime metadata keys

Use QuickTime keys to hold data in a Metadata atom.

Direction definition

Define a direction in metadata keys.

Metadata handling

Handling metadata in other file formats.

