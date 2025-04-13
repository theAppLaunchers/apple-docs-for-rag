

- QuickTime File Format
- Deprecated atoms
-  Sprite button behaviors 

Article

# Sprite button behaviors

Specify simple button behaviors for sprites in a sprite track.

## Overview

Important

Sprite media is deprecated in the QuickTime file format. The information that follows documents existing content containing sprite media and should not be used for new development.

In QuickTime 4 and later, sprites in a sprite track can specify simple button behaviors. These behaviors can control the sprite’s image, the system cursor, and the status message displayed in a Web browser. They also provide a shortcut for a common set of actions that may result in more efficient QuickTime movies.

Button behaviors can be added to a sprite. These behaviors are intended to make the common task of creating buttons in a sprite track easy — you basically just fill in a template.

Three types of behaviors are available; you may choose one or more behaviors. Each change a type of property associated with a button and are triggered by the mouse states `notOverNotPressed`, `overNotPressed`, `overPressed`, and `notOverPressed`. The three properties changed are:

- The sprite’s `imageIndex` value

- The ID of a cursor to be displayed

- The ID of a status string variable displayed in the URL status area of a Web browser.

Setting a property’s value to `–1` means don’t change it.

Note

The cursor is automatically set back to the default system cursor when leaving a sprite.

The sprite track handles letting one sprite act as an active button at a time.

The behaviors are added at the beginning of the sprite’s list of actions, so they may be overridden by actions if desired.

To use the behaviors, you fill in the new atoms as follows, using the description key specified in QT atom container description key:

```
kSpriteAtomType
    , 1

            [QTSpriteButtonBehaviorStruct]

            [QTSpriteButtonBehaviorStruct]

            [QTSpriteButtonBehaviorStruct]
```

## See Also

### Media data atom types

Sprite media

Sprite media is used to store character-based animation data in QuickTime movies.

Sprite track properties

Define properties that apply to an entire sprite track.

Sprite track media format

A media format for that stores sprite track information in atoms.

Sprite media atom and data types

Atoms that represent sprite media and data types.

QT atom container description key

Build QT atom container-based data structures.

Sprite media handler track properties QT atom container format

Set sprite media handler track properties in a QT atom container.

Sprite media handler sample QT atom container formats

Set sprite media handlers in QT atom containers.

Wired action grammar

Embed QT event handlers in their media samples.

Tween media

Store pairs of values to be interpolated between in QuickTime movies using tween media.

3D media

Store 3D image data in a base media in QuickTime movies.

VR media

Atoms that describe the QuickTime VR world.

Node parent atom

An atom that is the parent of one or more node ID atoms.

Node location atom structure ('nloc')

An atom that describes the type of a node and its location.

Deprecated

Custom cursor atom

An atom you use to replace the default cursors used by QuickTime VR.

Node information atom container

An atom container that includes general information about the node such as the node’s type, ID, and name.

