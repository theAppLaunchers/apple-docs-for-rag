

- QuickTime File Format
-  Panorama imaging atom Deprecated

Atom

# Panorama imaging atom

An atom describes the default imaging characteristics for all the panoramic nodes in a scene.

Deprecated

VR Media is deprecated in the QuickTime file format. The information that follows documents existing content containing VR Media and should not be used for new development.

## Overview

A panorama-imaging atom describes the default imaging characteristics for all the panoramic nodes in a scene. This atom overrides QuickTime VR’s own defaults.

The panorama-imaging atom has an atom type of `kQTVRPanoImagingAtomType` (`'impn'`). Generally, there is one panorama-imaging atom for each imaging mode, so the atom ID, while it must be unique for each atom, is ignored. QuickTime VR iterates through all the panorama-imaging atoms.

The structure of a panorama-imaging atom is defined by the `QTVRPanoImagingAtom` data type:

```
typedef struct QTVRPanoImagingAtom {
    UInt16                              majorVersion;
    UInt16                              minorVersion;
    UInt32                              imagingMode;
    UInt32                              imagingValidFlags;
    UInt32                              correction;
    UInt32                              quality;
    UInt32                              directDraw;
    UInt32                              imagingProperties[6];
    UInt32                              reserved1;
    UInt32                              reserved2;
} QTVRPanoImagingAtom, *VRPanoImagingAtomPtr;
```

The imagingValidFlags field in the panorama-imaging atom structure specifies which imaging property fields in that structure are valid. You can use these bit flags to specify a value for that field:

```
enum {
    kQTVRValidCorrection                        = 1 

**Constant descriptions**

`kQTVRValidCorrection`  
The default correction mode for panorama-imaging properties. If this bit is set, the correction field holds a default correction mode.

`kQTVRValidQuality`  
The default imaging quality for panorama-imaging properties. If this bit is set, the quality field holds a default imaging quality.

`kQTVRValidDirectDraw`  
The default direct-draw quality for panorama-imaging properties. If this bit is set, the directDraw field holds a default direct-drawing property.

`kQTVRValidFirstExtraProperty`  
The default imaging property for panorama-imaging properties. If this bit is set, the first element in the array in the imagingProperties field holds a default imaging property. As new imaging properties are added, they will be stored in this array.

## Topics

### Data fields

majorVersion

The major version number of the file format.

minorVersion

The minor version number of the file format.

imagingMode

The imaging mode to which the default values apply.

imagingValidFlags

A set of flags that indicate which imaging property fields in this structure are valid.

correction

The default correction mode for panoramic nodes.

quality

The default imaging quality for panoramic nodes.

directDraw

The default direct-drawing property for panoramic nodes.

imagingProperties

Reserved for future panorama-imaging properties.

reserved1

Reserved.

reserved2

Reserved.

## See Also

### Describing VR worlds

QTVR string atom

An atom that contains a string for QuickTime VR.

Deprecated

VR world atom container

An atom that contains name for the entire scene, the default node ID, and default imaging properties, as well as a list of the nodes contained in the QTVR track.

Deprecated

VR world header atom

An atom contains the name of the scene and the default node ID to be used when the file is first opened.

Deprecated

Imaging parent atom

An atom that is the parent atom of one or more node-specific imaging atoms.

Deprecated

