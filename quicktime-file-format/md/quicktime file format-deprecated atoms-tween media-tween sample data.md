

- QuickTime File Format
- Deprecated atoms
- Tween media
-  Tween sample data 

Article

# Tween sample data

## Overview

Tween sample data is stored in QT atom structures.

At the root level, there are one or more tween entry atoms; these atoms have an atom type value of `'twen'`. Each tween entry atom completely describes one interpolation operation. These atoms should be consecutively numbered starting at 1, using the atom ID field.

Each tween entry atom contains several more atoms that describe how to perform the interpolation. The atom ID field in each of these atoms must be set to 1.

Tween start atom (atom type is `'twst'`)  
This atom specifies the time at which the interpolation is to start. The time is expressed in the media’s time coordinate system. If this atom is not present, the starting offset is assumed to be 0.

Tween duration atom (atom type is `'twdu'`)  
This atom specifies how long the interpolation is to last. The time is expressed in the media’s time coordinate system. If this atom is not present, the duration is assumed to be the length of the sample.

Tween data atom (atom type is `'twdt'`)  
This atom contains the actual values for the interpolation. The contents depend on the value of the tween type atom.

Tween type atom (atom type is `'twnt'`)  
Describes the type of interpolation to perform.

The following table shows all currently defined tween types. All tween types are currently supported using linear interpolation.

| Tween type | Value | Tween data |
|----|----|----|
| 16-bit integer | `1` | Two 16-bit integers. |
| 32-bit integer | `2` | Two 32-bit integers. |
| 32-bit fixed-point | `3` | Two 32-bit fixed-point numbers. |
| Point: two 16-bit integers | `4` | Two points. |
| Rectangle: four 16-bit integers | `5` | Two rectangles. |
| QuickDraw region | `6` | Two rectangles and a region. The tween entry atom must contain a `'qdrg'` atom with an atom ID value of `1`. The region is transformed through the resulting matrices. |
| Matrix | `7` | Two matrices. |
| RGB color: three 16-bit integers | `8` | Two RGB colors. |
| Graphics mode with RGB color | `9` | Two graphics modes with RGB color. Only the RGB color is interpolated. The graphics modes must be the same. |

Each tween type is distinguished from other types by these characteristics:

- Input values or structures of a particular type

- A particular number of input values or structures (most often one or two)

- Output values or structures of a particular type

- A particular algorithm used to derive the output values

Tween operations for each tween type are performed by a tween component that is specific to that type or, for a number of tween types that are native to QuickTime, by QuickTime itself. Movies and applications that use tweening do not need to specify the tween component to use; QuickTime identifies a tween type by its tween type identifier and automatically routes its data to the correct tween component or to QuickTime.

When a movie contains a tween track, the tween media handler invokes the necessary component (or built-in QuickTime code) for tween operations and delivers the results to another media handler. The receiving media handler can then use the values it receives to modify its playback. For example, the data in a tween track can be used to alter the volume of a sound track.

Tweening can also be used outside of movies by applications or other software that can use the values it generates.

## See Also

### Storing tween media

Tween sample description

An atom that contains information for converting from media time to sample number to sample location for tweens.

Tween type categories

Tween QT atom container

Specify the characteristics of a tween with atoms in a tween QT atom container.

