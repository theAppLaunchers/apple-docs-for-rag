

- QuickTime File Format
- Storing and sharing media with QuickTime files
-  Atoms 

Article

# Atoms

The basic data unit in a QuickTime file is the atom.

## Overview

The basic data unit in a QuickTime file is the atom. Each atom contains size and type fields that precede any other data. The size field indicates the total number of bytes in the atom, including the size and type fields. The type field specifies the type of data stored in the atom and, by implication, the format of that data. In some cases, the size and type fields are followed by a version field and a flags field. An atom with these version and flags fields is sometimes called a *full atom*.

Note

An atom, as this documentation describes, is functionally identical to a *box*, as the ISO specifications describe for MPEG-4 and Motion JPEG-2000. An atom that includes version and flags fields is functionally identical to a *full box* as those specifications define.

Atom types are specified by a 32-bit unsigned integer, typically interpreted as a four-character ASCII code. Apple, Inc. reserves all four-character codes consisting entirely of lowercase letters. Unless otherwise stated, all data in a QuickTime movie is stored in big-endian byte ordering, also known as network byte ordering, in which the most significant bytes are stored and transmitted first.

Atoms are hierarchical in nature. That is, one atom can contain other atoms, which can contain still others, and so on. This hierarchy is sometimes described in terms of a parent, children, siblings, grandchildren, and so on. An atom that contains other atoms is called a *container atom*. The *parent atom* is the container atom exactly one level above a given atom in the hierarchy.

For example, a movie atom contains several different kinds of atoms, including one track atom for each track in the movie. The track atoms, in turn, contain one media atom each, along with other atoms that define other track characteristics. The movie atom is the parent atom of the track atoms. The track atoms are siblings. The track atoms are parent atoms of the media atoms. The movie atom is *not* the parent of the media atoms, because it is more than one layer above them in the hierarchy.

An atom that does not contain other atoms is called a *leaf atom*, and typically contains data as one or more fields or tables. Some leaf atoms act as flags or placeholders, however, and contain no data beyond their size and type fields.

The format of the data stored within a given atom cannot always be determined by the type field of the atom alone; the type of the parent atom may also be significant. In other words, a given atom type can contain different kinds of information depending on its parent atom. For example, the profile atom inside a movie atom contains information about the movie, while the profile atom inside a track atom contains information about the track. This means that all QuickTime file readers must take into consideration not only the atom type, but also the atom’s containment hierarchy.

## Atom layout

The following figure shows the layout of a sample atom. Each atom carries its own size and type information as well as its data. Leaf atoms contain data, usually in the form of tables.

A leaf atom, as shown in the preceeding figure, simply contains a series of data fields accessible by offsets.

Atoms within container atoms do not generally have to be in any particular order, unless such an order is specifically called out in this documentation. One such example is the handler description atom, which must come before the data being handled. For example, a media handler description atom must come before a media information atom, and a data handler description atom must come before a data information atom.

## Atom structure

Atoms consist of a header, followed by atom data. The header contains the atom’s size and type fields, giving the size of the atom in bytes and its type. It may also contain an extended size field, giving the size of a large atom as a 64-bit integer. If an extended size field is present, the size field is set to 1. The actual size of an atom cannot be less than 8 bytes (the minimum size of the type and size fields).

Some atoms also contain version and flags fields. These are sometimes called full atoms. The flag and version fields are not treated as part of the atom header in this documentation; they are treated as data fields specific to each atom type that contains them. Such fields must always be set to zero, unless otherwise specified.

An atom header consists of the following fields:

Atom size  
A 32-bit integer that indicates the size of the atom, including both the atom header and the atom’s contents, including any contained atoms. Normally, the `size` field contains the actual size of the atom, in bytes, expressed as a 32-bit unsigned integer. However, the `size` field can contain special values that indicate an alternate method of determining the atom size. (These special values are normally used only for media data (`'mdat'`) atoms.)

Two special values are valid for the `size` field:

- `0`, which is allowed only for a top-level atom, designates the last atom in the file and indicates that the atom extends to the end of the file.

- `1`, which means that the actual size is given in the `extended size` field, an optional 64-bit field that follows the `type` field. This accommodates media data atoms that contain more than 2^32 bytes.

The following figure shows how to calculate the size of an atom.

Type  
A 32-bit integer that contains the type of the atom. This can often be usefully treated as a four-character field with a mnemonic value, such as `'moov'` (`0x6D6F6F76`) for a movie atom, or `'trak'` (`0x7472616B`) for a track atom, but non-ASCII values (such as `0x00000001`) are also used. Knowing an atom’s type allows you to interpret its data. An atom’s data can be arranged as any arbitrary collection of fields, tables, or other atoms. The data structure is specific to the atom type. An atom of a given type has a defined data structure. If your application encounters an atom of an unknown type, it should not attempt to interpret the atom’s data. Use the atom’s `size` field to skip this atom and all of its contents. This allows a degree of forward compatibility with extensions to the QuickTime file format.

Warning

The internal structure of a given type of atom can change when a new version is introduced. Always check the version field, if one exists. Never attempt to interpret data that falls outside of the atom, as defined by the Size or Extended Size fields.

Extended size  
If the `size` field of an atom is set to 1, the `type` field is followed by a 64-bit `extended size` field, which contains the actual size of the atom as a 64-bit unsigned integer. This is used when the size of a media data atom exceeds 2^32 bytes.

When the `size` field contains the actual size of the atom, the `extended size` field is not present. This means that when a QuickTime atom is modified by adding data, and its size crosses the 2^32 byte limit, there is no `extended size` field in which to record the new atom size. Consequently, it is not always possible to enlarge an atom beyond 2^32 bytes without copying its contents to a new atom.

To prevent this inconvenience, media data atoms are typically created with a 64-bit placeholder atom immediately preceding them in the movie file. The placeholder atom has a type of `kWideAtomPlaceholderType` (`'wide'`).

Much like a `'free'` or `'skip'` atom, the `'wide'` atom is reserved space, but in this case the space is reserved for a specific purpose. If a `'wide'` atom immediately precedes a second atom, the second atom can be extended from a 32-bit size to a 64-bit size simply by starting the atom header 8 bytes earlier (overwriting the `'wide'` atom), setting the size field to 1, and adding an `extended size` field. This way the offsets for sample data do not need to be recalculated.

The `'wide'` atom is exactly 8 bytes in size, and consists solely of its `size` and `type` fields. It contains no other data.

Note

A common error is thinking that the `'wide'` atom contains the extended size. The `'wide'` atom is merely a placeholder that can be overwritten if necessary, by an atom header containing an `extended size` field.

## See Also

### Building in QuickTime

QT atoms and atom containers

An enhanced data structure that provide a more general-purpose storage format.

Creating, copying, and disposing of atom containers

Manage atoms in atom containers.

QuickTime movie files

The QuickTime file format describes the characteristics of QuickTime movie files.

