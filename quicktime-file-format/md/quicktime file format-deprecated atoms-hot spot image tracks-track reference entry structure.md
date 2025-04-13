

- QuickTime File Format
- Deprecated atoms
- Hot spot image tracks
-  Track reference entry structure 

Article

# Track reference entry structure

A data structure you use to specify information about any low-resolution image tracks contained in a movie.

## Overview

Since there are no fields in the pano sample data atom to indicate the presence of low-resolution image tracks, a separate sibling atom must be added to the panorama sample atom container. The track reference array atom contains an array of track reference entry structures that specify information about any low-resolution image tracks contained in a movie. Its atom type is `kQTVRTrackRefArrayAtomType` (‘tref’).

A track reference entry structure is defined by the QTVRTrackRefEntry data type:

```
typedef struct QTVRTrackRefEntry {
    UInt32                              trackRefType;
    UInt16                              trackResolution;
    UInt32                              trackRefIndex;
} QTVRTrackRefEntry;
```

**Field descriptions**

`trackRefType`  
The track reference type.

`trackResolution`  
The track resolution.

`trackRefIndex`  
The index of the track reference.

The number of entries in the track reference array atom is determined by dividing the size of the atom by `sizeof` (`QTVRTrackRefEntry`).

`kQTVRPreviewTrackRes` is a special value for the `trackResolution` field in the `QTVRTrackRefEntry` structure. This is used to indicate the presence of a special preview image track.

## See Also

### Hot spot image tracks

Low-resolution image tracks

Create low resolution image tracks for low memory conditions.

