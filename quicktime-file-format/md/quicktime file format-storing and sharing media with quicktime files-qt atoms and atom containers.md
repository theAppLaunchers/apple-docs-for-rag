

- QuickTime File Format
- Storing and sharing media with QuickTime files
-  QT atoms and atom containers 

Article

# QT atoms and atom containers

An enhanced data structure that provide a more general-purpose storage format.

## Overview

QT atoms are an enhanced data structure that provide a more general-purpose storage format and remove some of the ambiguities that arise when using simple atoms. A QT atom has an expanded header; the size and type fields are followed by fields for an atom ID and a count of child atoms.

This allows multiple child atoms of the same type to be specified through identification numbers. It also makes it possible to parse the contents of a QT atom of unknown type, by walking the tree of its child atoms.

QT atoms are normally wrapped in an *atom container*, a data structure with a header containing a lock count. Each atom container contains exactly one *root* atom, which is the QT atom. Atom containers are not atoms, and are not found in the hierarchy of atoms that makes up a QuickTime movie file. Atom containers may be found as data structures inside some atoms, however. Examples include media input maps and media property atoms.

Important

An *atom container* is *not* the same as a *container atom*. An atom container is a *container*, not an atom.

The following figure depicts the layout of a QT atom. Each QT atom starts with a QT atom container header, followed by the root atom. The root atom’s type is the QT atom’s type. The root atom contains any other atoms that are part of the structure.

Each container atom starts with a QT atom header followed by the atom’s contents. The contents are either child atoms or data, but never both. If an atom contains children, it also contains all of its children’s data and descendants. The root atom is always present and never has any siblings.

A QT atom container header contains the following data:

Reserved  
A 10-byte element that must be set to `0`.

Lock count  
A 16-bit integer that must be set to `0`.

Each QT atom header contains the following data:

Size  
A 32-bit integer that indicates the size of the atom in bytes, including both the QT atom header and the atom’s contents. If the atom is a leaf atom, then this field contains the size of the single atom. The size of container atoms includes all of the contained atoms. You can walk the atom tree using the size and child count fields.

Type  
A 32-bit integer that contains the type of the atom. If this is the root atom, the type value is set to `'sean'`.

Atom ID  
A 32-bit integer that contains the atom’s ID value. This value must be unique among its siblings. The root atom always has an atom ID value of `1`.

Reserved  
A 16-bit integer that must be set to `0`.

Child count  
A 16-bit integer that specifies the number of child atoms that an atom contains. This count includes only immediate children. If this field is set to `0`, the atom is a leaf atom and contains only data.

Reserved  
A 32-bit integer that must be set to `0`.

## QT atom containers

A QuickTime atom container is a basic structure for storing information in QuickTime. An atom container is a tree-structured hierarchy of QT atoms. You can think of a newly created QT atom container as the root of a tree structure that contains no children.

An atom container is a container, not an atom. It has a reserved field and a lock count in its header, not a size field and type field. Atom containers are not found in the atom hierarchy of a QuickTime movie file, because they are not atoms. They may be found as data inside some atoms, however, such as in media input maps, media property atoms, video effects sample data, and tween sample data.

A QT atom container contains QT atoms, as shown in the following figure. Each QT atom contains either data or other atoms. If a QT atom contains other atoms, it is a parent atom and the atoms it contains are its child atoms. Each parent’s child atom is uniquely identified by its atom type and atom ID. A QT atom that contains data is called a leaf atom.

Each QT atom has an offset that describes the atom’s position within the QT atom container. In addition, each QT atom has a type and an ID. The atom type describes the kind of information the atom represents. The atom ID is used to differentiate child atoms of the same type with the same parent; an atom’s ID must be unique for a given parent and type. In addition to the atom ID, each atom has a 1-based index that describes its order relative to other child atoms of the same parent with the same atom type. You can uniquely identify a QT atom in one of three ways:

- By its offset within its QT atom container

- By its parent atom, type, and index

- By its parent atom, type, and ID

You can store and retrieve atoms in a QT atom container by index, ID, or both. For example, to use a QT atom container as a dynamic array or tree structure, you can store and retrieve atoms by index. To use a QT atom container as a database, you can store and retrieve atoms by ID. You can also create, store, and retrieve atoms using both ID and index to create an arbitrarily complex, extensible data structure.

Warning

Since QT atoms are offsets into a data structure, they can be changed during editing operations on QT atom containers, such as inserting or deleting atoms. For a given atom, editing child atoms is safe, but editing sibling or parent atoms invalidates that atom’s offset.

Note

For cross-platform purposes, all data in a QT atom is expected to be in big-endian format. However, leaf data can be little-endian if it is custom to an application.

The following figure shows a QT atom container that has two child atoms. The first child atom (`offset = 10`) is a leaf atom that has an atom type of `'abcd'`, an ID of `1000`, and an index of `1`. The second child atom (`offset = 20`) has an atom type of `'abcd'`, an ID of `900`, and an index of `2`. Because the two child atoms have the same type, they must have different IDs. The second child atom is also a parent atom of three atoms.

The first child atom (`offset = 30`) has an atom type of `'abcd'`, an ID of `100`, and an index of `1`. It does not have any children, nor does it have data. The second child atom (`offset = 40`) has an atom type of `'word'`, an ID of `100`, and an index of `1`. The atom has data, so it is a leaf atom. The second atom (`offset = 40`) has the same ID as the first atom (`offset = 30`), but a different atom type. The third child atom (`offset = 50`) has an atom type of `'abcd'`, an ID of `1000`, and an index of `2`. Its atom type and ID are the same as that of another atom (`offset = 10`) with a different parent.

Note

If you are working with the QuickTime API, you do not need to parse QT atoms. Instead, the QT atom functions can be used to create atom containers, add atoms to and remove atoms from atom containers, search for atoms in atom containers, and retrieve data from atoms in atom containers.

Most QT atom functions take two parameters to specify a particular atom: the atom container that contains the atom, and the offset of the atom in the atom container data structure. You obtain an atom’s offset by calling either `QTFindChildByID` or `QTFindChildByIndex`. An atom’s offset may be invalidated if the QT atom container that contains it is modified.

When calling any QT atom function for which you specify a parent atom as a parameter, you can pass the constant `kParentAtomIsContainer` as an atom offset to indicate that the specified parent atom is the atom container itself. For example, you would call the `QTFindChildByIndex` function and pass `kParentAtomIsContainer` constant for the parent atom parameter to indicate that the requested child atom is a child of the atom container itself.

## See Also

### Building in QuickTime

Atoms

The basic data unit in a QuickTime file is the atom.

Creating, copying, and disposing of atom containers

Manage atoms in atom containers.

QuickTime movie files

The QuickTime file format describes the characteristics of QuickTime movie files.

